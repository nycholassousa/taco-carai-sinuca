# INDEX — Mapa de Docs

Leia só o que a tarefa exige.

| Doc | Quando ler |
|---|---|
| `GDD_MVP.md` | Regras de jogo, pontuação, conteúdo do MVP (cartas, bolas, mesa) |
| `ARCHITECTURE.md` | Pastas, rede, pipeline `ShotContext`, roadmap |
| `DECISIONS.md` | ADRs — decisões travadas; não alterar sem instrução |

## Estrutura planejada de `res://`
```
autoload/        # EventBus, NetworkManager, AudioManager (infra fina)
core/match/      # fluxo de partida, turnos, rodadas
core/scoring/    # FICHAS x MULT, foul
core/effects/    # ShotContext, hooks, EffectResource
data/            # .tres: bolas, passivas, buffs, debuffs, mesas, pickups
entities/        # bola, taco, mesa, caçapa, pickups
ui/              # HUD, loja, menus
assets/          # arte, áudio, fontes
```
Raiz atual: `project.godot`, `icon.svg`, `AGENTS.md`, `CLAUDE.md`, `.githooks/`.
