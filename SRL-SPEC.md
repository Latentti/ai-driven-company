# SRL - Serial Role Language

**Version 0.1.0** | **Latentti 2025**

---

## What is SRL?

SRL (Serial Role Language) is a token-efficient, role-based markup language designed for AI-assisted content generation. It bridges the gap between human speech transcripts and structured document generation.

SRL is optimized for:
- **LLM token efficiency** - Minimal syntax overhead
- **Role-based content** - Clear separation of narrator, frameworks, examples, dialogues
- **Generative workflows** - Direct mapping to BMad agents and document templates

---

## Design Principles

1. **Speech-first**: Designed to capture spoken ideas efficiently
2. **Role-explicit**: Every content block has an explicit role
3. **Framework-aware**: Native support for business frameworks (SWOT, Porter, etc.)
4. **Agent-compatible**: Direct mapping to BMad agent commands

---

## Syntax

### Document Header

```srl
@book <title> v<version>
@author <name>
@source <input-type>
@generator <tool>
@language <lang-code>
```

### Chapter Declaration

```srl
#ch<number> "<title>"
  @subtitle: <optional subtitle>
  @theme: <main theme>
```

### Content Roles

| Role | Syntax | Purpose |
|------|--------|---------|
| **@narrator** | `@narrator: <text>` | Main narrative voice |
| **@quote** | `@quote: <text>` | Highlighted quote or callout |
| **@framework** | `@framework <name>{params}` | Business framework reference |
| **@table** | `@table <name>[rows]{cols}` | Structured data (Toon-style) |
| **@diagram** | `@diagram <type>: <description>` | Mermaid diagram placeholder |
| **@scene** | `@scene <name>` | Narrative scene block |
| **@character** | `@character <name> <role>` | Person in scene |
| **@action** | `@action <description>` | What character does |
| **@reaction** | `@reaction "<quote>"` | Character response |
| **@list** | `@list <type>:` | Bullet or numbered list |
| **@section** | `@section "<title>"` | Sub-section within chapter |

### Framework Syntax

```srl
@framework track-comparison{track-a,track-b}
  track-a: "Korporaatiopolku"
    cost: "€50-150k"
    time: "3-4 months"
    learns: "Consultant"
  track-b: "Fast Track"
    cost: "€100"
    time: "30 min"
    learns: "Board"
```

### Table Syntax (Toon-inspired)

```srl
@table investments[3]{stream,cost,result}:
  Stream 1,€150-300k,Leadership Agent-Assisted
  Stream 2,€300-600k,T1-T2 Foundation
  Stream 3,€100-200k,AI Training + Champions
```

### Scene Syntax

```srl
@scene board-demo
  @setting: Board meeting, AI strategy on agenda
  @character Anna controller
  @action: shares screen, opens terminal
  @dialogue Anna: "Let me show you something..."
  @action: runs /biz-strategy-consultant
  @reaction board: "Anteeksi, mutta mitä?"
```

---

## Generation Pipeline

```
Speech → Speech-to-Clip → Transcript
                ↓
         SRL Structuring
                ↓
    BMad Agents (expansion)
                ↓
      Markdown Generation
                ↓
         PDF Rendering
```

---

## Example: Chapter 8 in SRL

```srl
@book AI-Driven-Company v1.0
@author Ari Hietamäki
@source speech-transcript
@generator bmad-agents
@language fi

#ch08 "Käytännön Aloitus"
  @subtitle: Strategia ilman toteutusta on hallusinaatio
  @theme: two-track-approach

  @section "8.1 Kaksi Polkua"
    @narrator: Olet lukenut seitsemän lukua teoriaa. Nyt on aika toimia.
    @narrator: Mutta miten toimia? Tässä kohtaa hallitukset jakautuvat.

    @framework track-comparison{corporate,fast-track}
      corporate:
        name: "Track A: Korporaatiopolku"
        approach: consultant-led
        cost: €50-150k
        time-to-results: 3-4 months
        who-learns: consultant
      fast-track:
        name: "Track B: Fast Track"
        approach: hands-on
        cost: €100
        time-to-results: 30 min
        who-learns: board

    @quote: Kuka oppii? Track A:ssa konsultti, Track B:ssä hallitus.

  @section "8.3 Track B: What The Fuck -hetki"
    @narrator: Perus chat ei riitä. Se ei vakuuta ketään.

    @scene board-demo
      @setting: Hallituksen kokous, AI-strategia asialistalla
      @character Anna controller
      @action: jakaa näytön, avaa terminaalin
      @dialogue Anna: "Käytin eilen tunnin opetellakseni uuden työkalun."
      @action: runs /biz-strategy-consultant
      @action: runs *competitive-analysis for Kilpailija Oy
      @time-elapsed: 15 min
      @result: 3-page strategic analysis
      @dialogue Chairman: "Tämän tekemiseen menisi analyytikolta viikko."
      @dialogue Anna: "Kyllä. Ja tämä maksoi 50 senttiä."
      @reaction Board: "Anteeksi, mutta mitä?"

  @section "8.9 Yhteenveto"
    @list key-messages:
      - Kaksi polkua: Korporaatio vs Fast Track
      - Kuka oppii? Konsultti vs Hallitus
      - Perus chat ei riitä - BMad-agentit 99% laatua
      - Yksi henkilö riittää näyttämään
      - Luku 9 jatkaa: asennus kaikille
```

---

## Tools

- **Speech-to-Clip**: Speech → Transcript (iOS/macOS)
- **SRL Parser**: SRL → Markdown (planned)
- **BMad Agents**: Content expansion and quality assurance

---

## License

MIT License - Latentti 2025

---

*SRL: From speech to structured documents, 100x faster.*
