# AGENTS.md — Taco Carai

## Contexto
Taco Carai: sinuca 2D top-down arcade caótica, 2-4 jogadores FFA. Estilo Balatro + estética
Boteco Brasileiro anos 90-2000 / Neon. Godot 4.7 (renderer Compatibility).
Multiplayer via Steam: ENet em dev -> GodotSteam em release.

## Anti-God-Class & Modularidade
- Máximo **250 linhas por `.gd`** (alvo <= 200). Passou disso: extrair componente/nó/helper.
- 1 responsabilidade por script/nó. Preferir composição de nós a herança profunda.
- `autoload/` só para infraestrutura fina (`NetworkManager`, `AudioManager`, `EventBus`).
  NUNCA colocar lógica de partida ou física em Autoload.

## Padrões GDScript
- Tipagem estática obrigatória: variáveis, parâmetros e retornos.
- Comunicação "Call down, signal up": pais chamam métodos dos filhos; filhos emitem sinais;
  eventos globais via `EventBus`.
- Cartas, passivas e bolas especiais são 100% Data-Driven (`Resource` + hooks do `ShotContext`).
  Nunca `if/elif` gigantes espalhados na física.
- Host-authoritative: só o host decide física/pontuação; clientes enviam intenção (input).

## Gestão de Contexto
- Consulte `docs/INDEX.md` antes de procurar arquivos; leia só os docs relevantes à tarefa.
- Nunca altere decisões de `docs/DECISIONS.md` sem instrução explícita.
- Não crie cenas/código fora do escopo pedido.

## Git
- Conventional Commits: `feat:`, `fix:`, `arch:`, `docs:`, `refactor:`, `chore:`.
- Nunca fazer commit ou push automaticamente, a menos que o prompt peça.
- Hooks em `.githooks/` (`git config core.hooksPath .githooks`): limite de 250 linhas,
  marcadores de conflito, arquivos > 10 MB.
