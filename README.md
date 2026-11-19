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

原 repo 只要更新了這裡已刪除的檔案（例如每天更新的星數圖）或 README，合併時就會出現衝突，需要手動處理。

第一次同步前，先加入原 repo：

```bash
git remote add upstream https://github.com/Raymondhou0917/speak-human-tw.git
```

每次同步：

```bash
git fetch upstream
```

```bash
git merge upstream/master
```

如果出現衝突，依 `git status` 顯示的狀態處理：

- 標示 `DU` 的檔案（這裡已刪除、原 repo 有修改）：再刪一次

  ```bash
  git rm <檔案路徑>
  ```

- `README.md` 標示 `UU`：保留這裡的版本

  ```bash
  git checkout --ours README.md
  ```

  ```bash
  git add README.md
  ```

全部處理完後提交：

```bash
git commit --no-edit
```

提交前確認兩件事：

- `SKILL.md` 的兩處修改仍在。原 repo 對 `SKILL.md` 其他段落的修改會自動合併進來。
- 原 repo 新增的檔案會一起進來。`references/` 裡的新檔要留著，其他用不到的新檔用 `git rm` 刪掉。
