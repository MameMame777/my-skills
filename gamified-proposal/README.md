# gamified-proposal

A Claude skill for writing and reviewing proposals (games, apps, learning tools, events) so that the target user *wants* to do it and *keeps* doing it. It checks a proposal against 10 items in dependency order, from background to retention risk, and uses the eight core drives of the Octalysis framework as an analysis lens for motivation. It has two modes: **create** (turn an idea into a proposal) and **review** (inspect an existing proposal or a released product, and compare the verdict with its public reception). The skill body is written in Japanese.

企画書を書く・レビューするためのスキルです。背景から継続リスクまでの10項目と、オクタリシスの8つの欲求を使って、対象者が「やりたくなる」「続けたくなる」企画かを検査し、執筆します。

## The 10 items

Each item depends on the one before it.

1. **背景 (As-is)**: the target user's current situation and frustrations, plus similar existing works and how this differs
2. **目指す姿 (To-be)**: the goal per target user, measured on the same scale as As-is
3. **Why**: the cause of the gap between As-is and To-be, in one sentence
4. **コンセプト (Concept)**: a one-sentence promise to the target user
5. **世界観 (World)**: why the core mechanic is natural in this world, and whether the tone matches the promise
6. **核の仕組み (Core mechanic)**: one action that delivers the concept, and how many drives it supports
7. **How / What**: How removes the cause from Why; What turns the core mechanic into features
8. **欲求 (Drives, Octalysis)**: which drive each What triggers, whether its conditions hold, and the White Hat / Black Hat balance
9. **体験描写 (Moments)**: the moment the user feels each drive, written from the user's point of view
10. **継続リスク (Retention risk)**: early, mid, and long-term risks of dropping off or of play turning into obligation

The skill also includes a list of common failures and an output template. The last section, marked 【任意】, holds the author's writing style (known → new sentence ordering). It is not part of the method, and you can delete it.

## Example prompts

**Create mode**

```
gamified-proposal で企画書を書いて。小学生が毎日5分、九九を練習したくなるアプリ。
```

**Review mode (your own proposal)**

```
この企画書を gamified-proposal でレビューして。できている項目・空いている項目・気になる点を出して。
（企画書を貼り付け）
```

**Review mode (an existing product, compared with public reception)**

```
gamified-proposal で「Minecraft」をレビューして。世間の評価（レビュー・販売数・継続率など）も調べて、スキルの判定と突き合わせて。
```

When the idea is still fragmentary, the skill returns the check result and asks you one question about the first decision to make, instead of writing the whole proposal at once.

## Install

### Claude Code (and other agents) via `npx skills`

Requires Node.js 22.20 or later.

```bash
# Install into the current project
npx skills add MameMame777/my-skills --skill gamified-proposal -a claude-code

# Install for all projects (user directory)
npx skills add MameMame777/my-skills --skill gamified-proposal -a claude-code -g
```

Leave out `-a claude-code` to choose agents interactively. See the [skills CLI reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) for all options.

To install by hand instead, copy the `gamified-proposal/` folder into `~/.claude/skills/` (all projects) or `.claude/skills/` (one project).

### claude.ai (zip upload)

1. Download `gamified-proposal.zip` from the [gamified-proposal-v1.0 release](https://github.com/MameMame777/my-skills/releases/tag/gamified-proposal-v1.0).
2. Make sure code execution is on: **Settings > Capabilities > Code execution and file creation** (Free, Pro, Max). On Team and Enterprise plans, your organization owner controls this.
3. Go to **Customize > Skills**, click **+**, choose **Create skill**, then **Upload a skill**, and select the zip.

See [Use Skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude) if the menu has moved.

## Known limitations

These are open questions, not settled parts of the method. Feedback and issues are welcome.

- Of the conditions in the drives table (item 8), only Loss & Avoidance has been checked in depth. The other seven are not yet well tested.
- A How can fix one problem and create another (for example, more freedom that makes difficulty harder to tune). It is not yet decided which item should catch this side effect.
- Similar works are treated as something to differentiate from. They could also be treated as competitors for the user's time and money.
- For buy-once works with an ending, users leaving is not a failure. The long-term check might be better asked as "do they play to the end?" or "do they want to recommend it?"
- There is no item for judging story quality.

When a review hits one of the last two, the skill reports it under "what the skill could not capture."

## Credits

- **Author**: MameMame777 ([Qiita](https://qiita.com/MameMame777)), created with Claude (Anthropic).
- **Octalysis framework**: the eight core drives and the White Hat / Black Hat distinction come from Yu-kai Chou's [Octalysis framework](https://yukaichou.com/gamification-examples/octalysis-complete-gamification-framework/). This skill uses the framework as an analysis lens. It is not affiliated with or endorsed by Yu-kai Chou.
- **Known → new ordering**: the optional writing rule is based on the given-new principle in linguistics, described in Haviland, S. E., & Clark, H. H. (1974). What's new? Acquiring new information as a process in comprehension. *Journal of Verbal Learning and Verbal Behavior*, 13, 512–521. ([publication list](https://web.stanford.edu/~clark/pubs.html))

## License

Licensed under the [MIT License](LICENSE).
