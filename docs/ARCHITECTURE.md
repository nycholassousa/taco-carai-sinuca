# ARCHITECTURE

## Pastas (`res://`)
`autoload/` · `core/match/` · `core/scoring/` · `core/effects/` · `data/` · `entities/` · `ui/` · `assets/`
(detalhes em `INDEX.md`). Limite: 250 linhas por `.gd`.

## Rede — Host-Authoritative
- Sobre `MultiplayerAPI` do Godot.
- Dev: `ENetMultiplayerPeer`. Release: `SteamMultiplayerPeer` (GodotSteam).
- Host simula física e pontuação; clientes enviam input (ângulo/força da tacada, escolhas de carta)
  e recebem estado. `NetworkManager` (autoload) só abstrai o peer.

## Pipeline de tacada (`ShotContext`)
Objeto que carrega o estado da tacada (fichas, mult, flags) e passa por hooks. Efeitos são
`Resource`s que implementam os hooks de que precisam:
1. `on_turn_start`
2. `on_shot_start`
3. `on_wall_bounce`
4. `on_ball_collision`
5. `on_ball_pocketed`
6. `on_shot_end` (aplica foul, fecha pontuação)

## Roadmap
1. **Fase 1 — Vertical Slice Solo:** mesa, bolas, taco, pontuação FICHAS × MULT.
2. **Fase 2 — Multiplayer Local ENet:** turnos, host-authoritative, 2-4 jogadores.
3. **Fase 3 — Cartas/Passivas/Loja:** motor de efeitos, conteúdo MVP.
4. **Fase 4 — Estética 90s + Steam:** arte/neon, áudio, GodotSteam.
