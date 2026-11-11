# Harnessed: An Eval Maze

*Same model. Different harness. Watch it escape — or run in circles.*

Every agent here runs the same model. What changes is its **harness**: the system prompt, the tools it can call, the skills it knows. Build a harness, send your agents into a maze, measure what helps, then promote the winners through an **eval gate** that rejects regressions.

**▶ Play:** https://anthonyc77.github.io/Harnessed-An-Eval-Maze/ *(once GitHub Pages is enabled)*

## How a turn works

1. **Run**: 30 agents using your production harness try to escape a maze. Pick any unlocked level, reroll the maze whenever you like. Each step, an agent picks one of its tools: look, compass, notebook, ask for directions, radar, clock…
2. **Evaluate**: behind the scenes, your harness replays every unlocked level 20 times. The learning loop then proposes **candidates**: add or remove a tool, upgrade the prompt, write a discovery into the guide. Each candidate is measured on its own, on the same mazes.
3. **Promote**: you are the human referee. You get limited slots and at most 1 addition and 1 removal per turn, or you can keep everything as it is. Use the 🪞 mirror to watch a candidate race your production harness on the same maze before you decide.
4. **Gate**: the new harness replays all levels. If any level drops by more than 10 points, the gate rejects it. If it passes, it ships as a new version and becomes the reference.
5. **Saturation**: once every level is above 90 %, the exam stops measuring anything. A harder level unlocks, along with one more slot and new cards: tools such as the clock, the radar or the full map, and new prompts.

## What's in the maze

- **Moving doors**: the clock tells the agent when they reopen.
- **Guards**: getting caught sends the agent back to the start. The radar spots them.
- **Pills**, placed at random:
  - 🔵 lets the agent eat guards;
  - 🟢 lets it walk through walls;
  - 🔴 *advertises* a shortcut to the exit, but actually scrambles the compass.

  An agent only knows what a pill does if its harness tells it. Otherwise it learns by swallowing one, and that discovery becomes a candidate you can promote into the guide.

## What it teaches

| In the game | In real agent work |
|---|---|
| Seven prompts (vague, hasty, frugal, right-hand rule, precise, think-aloud…) | System prompt design and its cost |
| Tools, slots | Tool selection; a limited context budget |
| Guide of pills | Skills and documentation |
| The red pill | A tool description that lies, like prompt injection |
| Token budget, full map | Cost of context |
| Candidates measured alone, one change per turn | Ablation studies |
| The mirror | A/B comparison with common random numbers |
| One run vs. 20 runs | Variance |
| The gate | Regression testing before release |
| Everyone scores 100 % | Eval saturation |

## Status

This is a **playable prototype**. The agents are simulated by rules in the browser: no LLM calls, no API key, no server. The interface is in French for now.

It is a single static `index.html`. [Three.js](https://threejs.org/) loads from a CDN, so you can open the file directly or serve it with GitHub Pages.
