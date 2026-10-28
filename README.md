# Skills

Claude skills by MameMame777. Each folder holds one skill (`<skill-name>/SKILL.md`), with its own README.

## Available skills

| Skill | Description | Install (Claude Code) |
|---|---|---|
| [gamified-proposal](gamified-proposal/) | Write or review a proposal (games, apps, learning tools, events) so the target user wants to do it and keep doing it. 10-item check plus Octalysis drives. Body in Japanese. | `npx skills add MameMame777/my-skills --skill gamified-proposal` |

## Install

### Claude Code (and other agents) via `npx skills`

Requires Node.js 22.20 or later.

```bash
# List the skills in this repo
npx skills add MameMame777/my-skills --list

# Install one skill into the current project
npx skills add MameMame777/my-skills --skill <skill-name> -a claude-code

# Add -g to install for all projects
npx skills add MameMame777/my-skills --skill <skill-name> -a claude-code -g
```

See the [skills CLI reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md) for all options.

### claude.ai (zip upload)

Each skill is published as a zip on the [Releases](https://github.com/MameMame777/my-skills/releases) page, in a release named `<skill-name>-v<version>`. Download the zip, then go to **Customize > Skills**, click **+**, choose **Create skill**, then **Upload a skill**. Code execution must be enabled under **Settings > Capabilities**. Details: [Use Skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

## Author

MameMame777 ([Qiita](https://qiita.com/MameMame777)). Skills were created with Claude (Anthropic). Third-party credits are in each skill's README.

## License

Licensed under the [MIT License](LICENSE).
