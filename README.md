# git-memo

## ローカルブランチをまとめて削除 (main以外)

```sh
git branch | grep -v "main" | xargs git branch -d
```

## mainブランチからfeaturesブランチへ逆マージ

```sh
git checkout main
git pull origin main
git checkout features/xxxxx
git merge main
git push origin features/xxxxx
```

## 作業中の変更を一時的に退避

```sh
// 退避した作業の一覧を確認
git stash list

// 変更を退避する
git stash -u

// 退避した作業を戻る
git stash apply 'stash@{0}'

// 退避した作業を消す
git stash drop 'stash@{0}'
```

## 過去の履歴をすべて削除

※普通はこんなことしないので個人開発で履歴をきれいにしたいときぐらいに使う

```sh
git checkout --orphan tmp
git commit -m "Initial Commit"
git checkout -B main
git push -f origin main
git branch -d tmp
```

## ブランチ操作

```sh
// ローカルブランチ一覧（カレントブランチには * が付く）
git branch

// リモートブランチ一覧
git branch -r

// 新規ブランチを作成
git branch <New Branch name>

// 既存ブランチの切替
git switch <Branch name>

// 新規ブランチを作成して切り替え
git switch -c <New Branch name>

// ブランチの削除（警告なしは -D を使用）
git branch -d <Branch name>
```
