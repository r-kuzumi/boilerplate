---
title: GitPressのProfile編集方法(how to edit profile on 2021)
date: 2021-01-09
tags: ["GitPress", "GitPressHelp"]
excerpt: "普通にプロフ更新しようとしたら失敗した。なのでその対処方法。"
---

# GitPressのProfile編集方法

GitPressのアカウントを取得したものの、プロフ更新に失敗したので対処方法のメモ。  
結論、プロフィール更新用のformのactionが変な値なのでこれを直す。

## バグ内容

- 対象ページ： /\[ユーザー\]/dashboard/profile
- 対象項目：Basic Profile および Social の Save ボタン
- 発生事象
  - GitPressの404ページに遷移する
  - プロフィールの更新が行われない

## 原因

- form の action属性が /\[ユーザー\]/settings/profile?part=\*\*\* になっている
  - このURLが存在しない
  - なんとなく旧URLな感じがする

## 対策

- 開発者コンソールなどで、form の action属性を /\[ユーザー\]/dashboard/profile?part=\*\*\* にする
- 書き換えた状態で Save ボタンを押せばよい

## 補足

- 修正後URLにPOSTすると、レスポンスは Nginx の 404 が返ってくる
  - GitPressの404ページではない
- 失敗している印象っぽいが、内部処理はちゃんとされてプロフ更新はされるみたい
