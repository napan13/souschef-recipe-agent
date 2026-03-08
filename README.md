# SousChef Recipe Agent

An AI agent that transforms raw recipe text into structured,
beginner-friendly cooking instructions.

## How it works
1. Paste any recipe text as input
2. Node 1 extracts structured data (ingredients, steps, metadata)
3. Node 2 critiques quality, clarity, units and variant
4. Node 3 refines based on the critique
5. Output is exported as JSON

## Setup
1. Open the notebook in Google Colab
2. Run the first cell to install dependencies
3. Add your GROQ API key where indicated
4. Run all cells
5. Paste a recipe when prompted

## Agent design
- Node 1 (Extractor): pulls all data from raw recipe text as-is
- Node 2 (Critic): checks step clarity, units, variant, difficulty
- Node 3 (Refiner): applies all fixes from the critique

## Model
- LLM: Llama 3 via Groq API
- Framework: LangGraph + Pydantic

## Example outputs
See the /example_outputs folder for JSON results from 10 test recipes.

## Evaluation
Tested on 10 varied recipes including meat, vegan, fish, baking,
and recipes with imperial units.

## What worked
- Critique/repair loop improved step clarity reliably
- Variant detection (vegan/meat/fish) was consistently accurate
- fix_units() function reliably handled unit conversion in code

## What failed
- Unit enforcement via prompt alone was unreliable
- Model occasionally returned invalid difficulty values

## What I would improve
- Add serving size scaling
- Add confidence scoring per step
- Connect to SousChef API endpoint directly
```

---

**Step 9 — Final check**
Your repo should look like:
```
souschef-recipe-agent/
├── README.md
├── souschef_recipe_agent.ipynb
└── example_outputs/
    ├── chicken_rice.json
    ├── pancake.json
