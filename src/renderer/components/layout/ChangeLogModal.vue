<template lang="pug">
material-modal(:show="isShowChangeLog" max-width="60%" @close="isShowChangeLog = false")
  main(:class="$style.main")
    h2 当前版本更新日志
    div.scroll.select(:class="$style.info")
      div(:class="$style.current")
        h3 当前版本：{{ versionInfo.version }}
        template(v-if="info.desc")
          h3 版本变化：
          pre(:class="$style.desc" v-text="info.desc")
      div(v-if="info.history.length" :class="[$style.history, $style.desc]")
        h3 历史版本：
        div(v-for="(ver, index) in info.history" :key="index" :class="$style.item")
          h4 v{{ ver.version }}
          pre(v-text="ver.desc")
</template>

<script>
import { compareVer } from '@common/utils'
import { clipboardWriteText } from '@common/utils/electron'
import { versionInfo, isShowChangeLog } from '@renderer/store'
import { getLastStartInfo } from '@renderer/utils/ipc'
import { computed, ref } from '@common/utils/vueTools'

export default {
  setup() {
    const lastStartVersion = ref(null)
    void getLastStartInfo().then(version => {
      lastStartVersion.value = version
    })

    const normalizeDesc = desc => {
      if (!desc) return ''
      return desc
        .replace(/^[\s\S]*?(?=^\s*(?:新增|优化|修复|变更|移除|其他|开放API变更|不兼容性变更|不兼容性变更说明)\s*$)/m, '')
        .replace(/\s*[（(]#\d+[^）)]*[）)]/g, '')
        .replace(/\n{3,}/g, '\n\n')
        .trim()
    }

    const info = computed(() => {
      const currentVer = process.versions.app
      const lastStartVer = lastStartVersion.value
      const info = {
        version: '',
        desc: '',
        history: [],
        isLatest: true,
      }
      if (!versionInfo.newVersion?.history) return info
      info.isLatest = compareVer(currentVer, versionInfo.newVersion.version) >= 0

      const history = [{ version: versionInfo.newVersion.version, desc: versionInfo.newVersion.desc }, ...versionInfo.newVersion.history]

      if (lastStartVer) {
        for (const ver of history) {
          switch (compareVer(ver.version, currentVer)) {
            case 0:
              info.version = ver.version
              info.desc = normalizeDesc(ver.desc)
              break
            case -1:
              if (compareVer(lastStartVer, ver.version) < 0) {
                info.history.push({
                  ...ver,
                  desc: normalizeDesc(ver.desc),
                })
              }
          }
        }
      } else {
        const verInfo = history.find(v => v.version == currentVer)
        if (verInfo) {
          info.version = verInfo.version
          info.desc = normalizeDesc(verInfo.desc)
        } else {
          info.desc = '未找到当前版本的更新日志'
          info.version = currentVer
        }
      }

      return info
    })
    return {
      clipboardWriteText,
      versionInfo,
      info,
      isShowChangeLog,
    }
  },
}
</script>


<style lang="less" module>
@import '@renderer/assets/styles/layout.less';

.main {
  position: relative;
  padding: 15px 0;
  min-width: 300px;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  overflow: hidden;
  * {
    box-sizing: border-box;
  }
  h2 {
    flex: 0 0 none;
    font-size: 16px;
    color: var(--color-font);
    line-height: 1.3;
    text-align: center;
    margin-bottom: 15px;
  }
  h3 {
    font-size: 14px;
    line-height: 1.3;
  }
  pre {
    white-space: pre-wrap;
    text-align: justify;
    margin-top: 10px;
  }
}

.info {
  flex: 1 1 auto;
  font-size: 14px;
  line-height: 1.5;
  overflow-y: auto;
  height: 100%;
  padding: 0 15px;
}
.current {
  > p {
    padding-left: 15px;
  }
}

.desc {
  h3, h4 {
    font-weight: bold;
  }
  h3 {
    padding: 5px 0 3px;
  }
  ul {
    list-style: initial;
    padding-inline-start: 30px;
  }
  p {
    font-size: 14px;
    line-height: 1.5;
  }
}

.history {
  h3 {
    padding-top: 15px;
  }

  .item {
    h3 {
      padding: 5px 0 3px;
    }
    padding: 0 15px;
    + .item {
      padding-top: 15px;
    }
    h4 {
      font-weight: 700;
    }
    > p {
      padding-left: 15px;
    }
  }
}
</style>
