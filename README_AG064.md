# OpenSpace (AG064 Fork)

**Forked from:** [HKUDS/OpenSpace](https://github.com/HKUDS/OpenSpace)
**Purpose:** Self-evolving skills engine for AG-Claw agents
**LLM:** MiniMax-M2.7 via api.minimax.io (sk-cp- key)

## Quick Start

### 1. Configure MiniMax API Key

```bash
export MINIMAX_API_KEY='your-sk-cp-key'
export MINIMAX_API_BASE='https://api.minimax.io/v1'
export MINIMAX_MODEL='MiniMax-M2.7'
export OPENSPACE_MODEL='minimax/MiniMax-M2.7'
```

### 2. Install

```bash
pip install git+https://github.com/AG064/OpenSpace.git --no-deps --break-system-packages
```

### 3. Test

```bash
openspace --query "Say 'OK' in one word" --no-ui
```

## OpenSpace CLI

```bash
# Single query mode
openspace --query "Your task here" --no-ui

# Interactive mode
openspace --interactive

# Custom model
openspace --model minimax/MiniMax-M2.7 --query "Your task"
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `MINIMAX_API_KEY` | MiniMax API key (sk-cp-...) |
| `MINIMAX_API_BASE` | MiniMax endpoint (https://api.minimax.io/v1) |
| `MINIMAX_MODEL` | Model name (MiniMax-M2.7) |
| `OPENSPACE_MODEL` | OpenSpace LLM model (minimax/MiniMax-M2.7) |
| `LITELLM_ENDPOINT` | Custom LLM endpoint (for local models) |

## AG-Claw Integration

See: [AG064/ag-claw](https://github.com/AG064/ag-claw) → `src/features/skill-evolution/`

```typescript
import { SkillEvolution } from './features/skill-evolution';

const se = new SkillEvolution({
  apiKey: 'sk-cp-your-key',
  llmProvider: 'minimax',
  openSpacePath: '/home/user/OpenSpace',
});

await se.fixSkill('/path/to/skill/SKILL.md');
await se.evolveSkill('my-skill');
```

## Skills Directory

Skills are stored in: `~/.openclaw/skills/`

Each skill has:
- `SKILL.md` — definition and instructions
- `.skill_id` — unique identifier
- `metrics.json` — usage metrics (auto-generated)

## Status

- [x] Forked from HKUDS/OpenSpace
- [x] Torch dependency removed (not needed with cloud LLM)
- [x] MiniMax-M2.7 working via api.minimax.io
- [x] litellm integration working
- [x] OpenSpace CLI working with MiniMax
- [x] Pushed to github.com/AG064/OpenSpace
