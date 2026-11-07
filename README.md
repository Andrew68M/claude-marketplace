# andrew68m-plugins

Môj osobný marketplace pre Claude: všetky skilly a pluginy z mojich forkov na jednom mieste.

## Pridanie do Claude (raz)

**Claude Desktop, záložka Code:** bočný panel → Plugins → `+` → Browse plugins → dropdown „By Anthropic“ → **Add marketplace from GitHub** → `Andrew68M/claude-marketplace` → Sync.

**Chat / Cowork:** Customize → Plugins → Personal plugins `+` → Add marketplace → Add from a repository → `Andrew68M/claude-marketplace`.

**Terminál (Claude Code):**

```bash
claude plugin marketplace add Andrew68M/claude-marketplace
claude plugin install unslop@andrew68m-plugins
```

## Čo obsahuje

| Plugin | Zdroj | Čo robí | Poznámka |
|---|---|---|---|
| `unslop` | [Andrew68M/unslop](https://github.com/Andrew68M/unslop) | Prerobí UI, ktoré vyzerá ako od AI, na navrhnuté rozhranie | Snapshot a video potrebujú Playwright (a ffmpeg) |
| `agent-skills` | [Andrew68M/agent-skills](https://github.com/Andrew68M/agent-skills) | 34 inžinierskych skillov a 4 agenti (spec → ship) od Addyho Osmaniho | |
| `ponytail` | [Andrew68M/ponytail](https://github.com/Andrew68M/ponytail) | Režim „lenivý senior dev“: najjednoduchšie riešenie, ktoré funguje | Má hooky, nastavenie cez `/plugin configure` |
| `prompts-chat` | [Andrew68M/prompts.chat](https://github.com/Andrew68M/prompts.chat) | Hľadanie promptov a skillov z prompts.chat | Pripája MCP server `https://prompts.chat/api/mcp`. Skopírovaný v `plugins/prompts-chat/` (pôvodný názov s bodkou aplikácia neprijímala) |
| `omniroute-skills` | [Andrew68M/OmniRoute](https://github.com/Andrew68M/OmniRoute) | 45 skillov na ovládanie AI gateway OmniRoute (bez duplicitného ponytail) | Užitočné iba vtedy, keď máš OmniRoute nainštalovaný |
| `graphify` | [Andrew68M/graphify](https://github.com/Andrew68M/graphify) (vetva `v8`) | Urobí z priečinka znalostný graf | Potrebuje CLI: `uv tool install graphifyy` |

## Aktualizácie

Šesť pluginov sa sťahuje priamo z mojich forkov. Keď fork synchronizujem s originálom (na GitHube cez „Sync fork“) a v Claude dám Update, dostanem novú verziu.

`graphify` a `prompts-chat` sú výnimky a sú skopírované priamo v tomto repozitári. Skill graphify je skopírovaný v `plugins/graphify/`, lebo v repozitári nie je uložený vo formáte, ktorý by Claude vedel načítať priamo. Pri aktualizácii treba skopírovať `graphify/skill.md` → `plugins/graphify/skills/graphify/SKILL.md` a `graphify/skills/claude/references/` → `plugins/graphify/skills/graphify/references/`.

## Pridanie ďalšieho pluginu

Pridaj položku do `.claude-plugin/marketplace.json`, napríklad:

```json
{ "name": "nazov", "source": { "source": "github", "repo": "Andrew68M/nazov" } }
```

Ak repozitár nemá `.claude-plugin/plugin.json`, doplň `"strict": false` a `"skills": ["./skills/nazov"]`.

## Licencie

Každý plugin má licenciu svojho autora: unslop CC BY 4.0 (Damir Sokolovsky), graphify Apache-2.0 (licencia a NOTICE sú v `plugins/graphify/`), ostatné pozri v ich repozitároch.
