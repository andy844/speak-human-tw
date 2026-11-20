# speak-human-tw（精簡版）

這是 [Raymondhou0917/speak-human-tw](https://github.com/Raymondhou0917/speak-human-tw) 的 fork，只保留 AI 載入 skill 需要的檔案，方便直接放進 skills 目錄使用。

原作者：Raymond Hou（雷蒙三十），以 MIT 授權釋出，授權全文見 [LICENSE](LICENSE)。

## 保留的檔案

- `SKILL.md`：skill 本體
- `references/`：`SKILL.md` 會引用的參考資料
- `LICENSE`：原作者的 MIT 授權聲明

## 刪掉的內容

以下檔案在載入 skill 時用不到，所以刪掉了。想看完整內容請到原 repo。

- 原本的 README、CHANGELOG、CONTRIBUTING
- `assets/`：README 用的展示圖與星數成長圖
- `evals/`：評測用例與結果
- `install/`：各工具的安裝說明
- `scripts/` 與 `.github/`：自動更新星數圖的腳本、排程與 issue 範本

## 對 `SKILL.md` 的修改

和原版相比只改了兩處，同步原 repo 時要保留：

1. 刪除「參考導航」最後一行指向 `evals/` 的連結（資料夾已刪除，連結會失效）
2. 刪除 frontmatter 的 `changelog` 欄位（版本紀錄，執行時用不到）

## 同步原 repo

不要在 GitHub 網頁按 Sync fork。這個 fork 刪掉的檔案原 repo 還在更新，網頁合併不了，只會提示「Discard commits」，按下去這裡的修改會全部被原 repo 的版本蓋掉。

第一次同步前，先加入原 repo：

```bash
git remote add upstream https://github.com/Raymondhou0917/speak-human-tw.git
```

之後每次同步，在 repo 根目錄依序執行：

```bash
git fetch upstream
git merge --no-commit upstream/master
git checkout HEAD -- README.md
git ls-files | grep -vE '^(SKILL\.md|LICENSE|README\.md|references/)' | xargs git rm -q -f --
git commit --no-edit
```

`git merge` 這行印出 CONFLICT 是正常的，後面幾行會處理掉：

- 只收原 repo 對 `SKILL.md`、`references/`、`LICENSE` 的更新，`references/` 裡的新檔也會一起進來
- `README.md` 留這裡的版本
- 其他檔案（例如每天更新的星數圖、新加的說明文件）一律刪掉

原 repo 剛好改到上面那兩處 `SKILL.md` 修改的附近時，`SKILL.md` 會留著衝突標記，`git commit` 會失敗。這時打開 `SKILL.md` 處理衝突、保留那兩處修改，再執行：

```bash
git add SKILL.md
```

```bash
git commit --no-edit
```
