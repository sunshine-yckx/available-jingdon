# **不要 fork, 不要 fork, 不要 fork, 请点亮 star**

# **已经有这么多大佬不再维护 GitHub 上的代码了, 你们为什么还要 fork 呢?**

# 特别声明:

- 本仓库发布的 MyActions 项目中涉及的任何解锁和解密分析脚本, 仅用于测试和学习研究, 禁止用于商业用途, 不能保证其合法性, 准确性, 完整性和有效性, 请根据情况自行判断.

- 本项目内所有资源文件, 禁止任何公众号、自媒体进行任何形式的转载、发布.

- HenryTSZ 对任何脚本问题概不负责, 包括但不限于由任何脚本错误导致的任何损失或损害.

- 间接使用脚本的任何用户, 包括但不限于建立 VPS 或在某些行为违反国家/地区法律或相关法规的情况下进行传播, HenryTSZ 对于由此引起的任何隐私泄漏或其他后果概不负责.

- 请勿将 MyActions 项目的任何内容用于商业或非法目的, 否则后果自负.

- 如果任何单位或个人认为该项目的脚本可能涉嫌侵犯其权利, 则应及时通知并提供身份证明, 所有权证明, 我们将在收到认证文件后删除相关脚本.

- 任何以任何方式查看此项目的人或直接或间接使用该 MyActions 项目的任何脚本的使用者都应仔细阅读此声明. HenryTSZ 保留随时更改或补充此免责声明的权利. 一旦使用并复制了任何相关脚本或 MyActions 项目的规则, 则视为您已接受此免责声明.

  **您必须在下载后的 24 小时内从计算机或手机中完全删除以上内容.** </br>

  > **_您使用或者复制了本仓库且本人制作的任何脚本，则视为 `已接受` 此声明，请仔细阅读_**

## 使用教程

如果以前使用 `sazs34` 大佬的方式, 修改 `.github/workflows/repo-sync.yml` 为如下代码即可:

```yml
# File: .github/workflows/repo-sync.yml
name: sync-HenryTSZ-scripts
on:
  schedule:
    - cron: '5 15 * * *'

  workflow_dispatch:
  watch:
    types: started
  repository_dispatch:
    types: sync-HenryTSZ-scripts
jobs:
  repo-sync:
    env:
      PAT: ${{ github.event.client_payload.PAT || secrets.PAT }} #此处PAT需要申请，教程详见：https://www.jianshu.com/p/bb82b3ad1d11
    runs-on: ubuntu-latest
    if: github.event.repository.owner.id == github.event.sender.id
    steps:
      - uses: actions/checkout@v2

        with:
          persist-credentials: false

      - name: sync HenryTSZ-scripts

        uses: repo-sync/github-sync@v2
        if: env.PAT
        with:
          source_repo: 'https://github.com/HenryTSZ/MyActions.git'
          source_branch: 'main'
          destination_branch: 'main'
          github_token: ${{ github.event.client_payload.PAT || secrets.PAT }}
```

其余请按照如下方式进行

1. [按照这个教程进行 reposync](backup/reposync.md)
2. 再在`Settings`-`Secrets`里面添加`JD_COOKIE`
3. 多条 cookie 用`&`隔开, 支持无数条 cookie
4. 前三步之后，点击一下右上角的 star（fork 左边那个），让 workflow 运行一次。

(时效性较慢)更多 Secrets 配置[点击查看](backup/secrets.md)

(时效性较快)lxk0301-Secrets 配置[点击查看](https://gitee.com/lxk0301/jd_scripts/blob/master/githubAction.md)

> 具体如何取 cookie 如何配置, 可参考 [浏览器获取京东 cookie 教程](https://gitee.com/lxk0301/jd_scripts/blob/master/backUp/GetJdCookie.md) 或 [浏览器插件获取京东 cookie 教程](https://gitee.com/lxk0301/jd_scripts/blob/master/backUp/GetJdCookie2.md)

### 赞赏码(维护不易, 请赏杯茶水费)

<div align=center>
<img width="250" height="250" src="//gitee.com/henrytsz/jd_scripts/raw/master/icon/thanks-vx.JPG"/>
<img width="250" height="250" src="https://gitee.com/henrytsz/jd_scripts/raw/master/icon/thanks-zfb.JPG"/>
</div>
