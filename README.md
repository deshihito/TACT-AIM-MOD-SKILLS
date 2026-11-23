# TACT-AIM-MOD-SKILLS

TACT-AIM 系 MOD（`TACT-AIM-MOD` / `TACT-AIM-MYTHOLOGY` など）にコンテンツを
追加するための、エージェント向けスキル集です。

新武器・新アイテム・新キャラ・新概念（新システム）を追加するときの
**流儀（どう作るか）**、**追加時に必要な確認項目**、**SVG イラスト（コスチューム）を
作るときの流儀**、そして **sb3 の往復検証ゲート** を、実際に MOD を作る中で
踏んだ事故と実測に基づいてスキル化してあります。

原作は uk-400 の Scratch 作品「TACT-AIM 16.8」（project 831274817）です。
蒸留版（原作の純粋な TS 移植）は `TACT-AIM-distilled`、MOD はそちらには入れず
MOD 側レポで行うのが原則です。

## スキル一覧

| スキル | 内容 |
|---|---|
| [tact-aim-add-content](skills/tact-aim-add-content/SKILL.md) | 総合手順。追加の種類によらない全体の流れ、検証ゲート、落とし穴一覧、State E〜I の教訓 |
| [tact-aim-add-weapon](skills/tact-aim-add-weapon/SKILL.md) | 新武器（メイン武器）の追加: Item_list / Bullet_list、反動、連鎖・特殊挙動、ショップカード |
| [tact-aim-add-item](skills/tact-aim-add-item/SKILL.md) | 新アイテム（サブ武器・設置物・ガード系）の追加: チャージ経済、ガード、起爆信号、派生（ライト版） |
| [tact-aim-add-character](skills/tact-aim-add-character/SKILL.md) | 新キャラの追加: Character_2 / Character_tree、ツリー連結、起動時上書きの罠、バナー |
| [tact-aim-add-concept](skills/tact-aim-add-concept/SKILL.md) | 新概念・新システムの追加: スーパースキル、スキン段階、バフ、NPC/モード、クラウド形式の制約 |
| [tact-aim-svg-costumes](skills/tact-aim-svg-costumes/SKILL.md) | SVG イラスト / コスチュームの流儀: 顔の向き、原作パレット、キャンバスと回転中心、登録2箇所 |
| [tact-aim-sb3-round-trip](skills/tact-aim-sb3-round-trip/SKILL.md) | sb3 往復検証: 構造検証 0 件、ダイジェスト、TurboWarp IR エラーの切り分け |

共通の確認項目だけをすぐ見たいときは
[checklists/add-content-checklist.md](checklists/add-content-checklist.md) をどうぞ。

## 使い方

各スキルは `SKILL.md`（YAML frontmatter の `name` / `description` ＋本文）と
`skill.yaml` の組です。使っているエージェントのスキル置き場
（例: `~/workspace/custom-skills/` や `~/.claude/skills/`）へ、
フォルダごとコピーして使ってください。

```
cp -r skills/tact-aim-add-weapon <your-skills-dir>/
```

## 大原則（全スキル共通）

1. **仕組みを実測で確認してから触る。** レコード形式・連結規則・フック位置は
   推測で書かず、既存データとコードから実測する。
2. **順番は データ → ロジックフック → コスチューム → テスト → sb3 再生成 → push。**
3. **仕様の数値・デザイン判断は作者（人間）が決める。** 未指定の値は仮置きとして
   実装し、報告で「仮置き」と明示する。勝手に確定しない。
4. **検証ゲートを全部通して初めて push。** `npm test` 全合格、起動ダイジェストの
   再基準化（新旧の全比較で差分が追加由来だけであることの確認）、
   `detranspile:check-distilled`、sb3 構造検証 0 件、往復検証 PASS。
5. **蒸留版（原作の純粋コピー）には MOD の追加を入れない。**

## ライセンス

CC BY-SA 2.0（[LICENSE](LICENSE)）。

これは Scratch 作品のライセンスです。Scratch に公開された作品は Scratch の
利用規約により原則 CC BY-SA 2.0 となり、原作「TACT-AIM 16.8」も同ライセンスです。
改変物を配布する場合は、原作者クレジットの表示と、同ライセンスでの継承が必要です。
詳細は [NOTICE.md](NOTICE.md) を参照してください。
