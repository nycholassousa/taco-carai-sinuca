# DECISIONS

| ID | Decisão |
|---|---|
| ADR-001 | 2D Top-Down Estilizado + renderer Compatibility |
| ADR-002 | Host-Authoritative via MultiplayerAPI (ENet dev -> GodotSteam release) |
| ADR-003 | Motor de efeitos Data-Driven (`Resource` + `ShotContext`) |
| ADR-004 | Debuffs no próprio turno, anúncio público, limite de 2 acumulados |
| ADR-005 | Foul zera pontos da tacada; vitória por soma em 5 rodadas |

## ADR-001 — 2D Top-Down + Compatibility
Visual 2D estilizado; renderer Compatibility para máxima compatibilidade e baixo custo. 3D descartado.

## ADR-002 — Host-Authoritative
Host decide física e pontos via `MultiplayerAPI`. ENet em dev, trocado por `SteamMultiplayerPeer`
(GodotSteam) em release sem mudar a lógica de jogo.

## ADR-003 — Efeitos Data-Driven
Cartas/passivas/bolas especiais são `Resource`s com hooks do `ShotContext`. Sem `if/elif` na física.

## ADR-004 — Debuffs
Debuff é jogado no próprio turno do autor, com anúncio público "X jogou Y em Z". Máx 2 debuffs por alvo.

## ADR-005 — Foul e vitória
Matar a Bola Branca zera os pontos da tacada e dá Bola na Mão ao próximo. Vence a maior soma após 5 rodadas.
