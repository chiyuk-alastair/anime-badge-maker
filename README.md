# Anime Badge Maker

[简体中文](README.zh-CN.md) | English

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Codex Skill](https://img.shields.io/badge/Codex-Agent%20Skill-111827.svg)

A reusable Agent Skill for turning anime character screenshots, GK/collectible figure photographs, and multi-angle references into polished circular badge artwork—and then placing the approved artwork into a photoreal physical button badge mockup.

The project encodes a practical visual standard: character identity and anatomy come before spectacle. It explicitly guards against common generation failures such as importing another character's hand, changing a closed eye to an open eye, inventing accessories, compressing a full body into an awkward circle, or pasting flat artwork onto a photographed badge.

## What it produces

With a simple request such as:

```text
Use $anime-badge-maker to make this reference into a badge.
```

the default workflow returns:

1. `01-badge-art.png` — a square canvas with a circular anime badge composition.
2. `02-badge-mockup.png` — the same approved artwork composited into a physical button badge photograph.

Users may request only one stage:

- “Artwork only” runs the illustration stage.
- “Put this design into the badge” runs the physical mockup stage without redesigning the character.

## Key capabilities

- Classifies uploads as character references, finished badge art, or physical badge photographs.
- Assigns different evidence roles to front, profile, full-body, hand, and accessory references.
- Builds an internal ownership map before generation so background limbs and props are not assigned to the subject.
- Preserves hairstyle, eye state, expression, facial markings, clothing, accessories, pose, and body type.
- Selects bust or half-body framing when a full-body crop would damage proportions.
- Keeps backgrounds readable inside a circular crop without overpowering the character.
- Preserves metal rim, curvature, perspective, reflections, highlights, shadows, and photographic texture in mockups.
- Applies a hard-gate quality checklist and performs targeted retries instead of accepting obvious defects.
- Supports implicit activation through its description and explicit activation with `$anime-badge-maker`.

## Requirements

- Codex, ChatGPT desktop, or another Agent Skills-compatible host.
- An available image-generation and image-editing capability.
- One or more character reference images for artwork generation.
- Optional: a physical badge photograph. If omitted, the included blank badge photograph is used.

No API key, Python package, or command-line dependency is required by the Skill itself. Image availability and usage limits depend on the host application.

## Installation

### Install with Codex Skill Installer

In Codex, enter:

```text
$skill-installer Install the skill from https://github.com/chiyuk-alastair/anime-badge-maker/tree/main/skills/anime-badge-maker
```

If the Skill does not appear immediately after installation, restart Codex.

### Manual installation

Clone the repository:

```bash
git clone https://github.com/chiyuk-alastair/anime-badge-maker.git
```

Copy `skills/anime-badge-maker` into your user-level skills directory. Current Codex documentation lists:

```text
$HOME/.agents/skills/anime-badge-maker
```

Some Codex builds or configured environments use `$CODEX_HOME/skills` (commonly `$HOME/.codex/skills`). Use the location already recognized by your host.

### Repository-scoped use

To make the Skill available only inside one repository, copy it to:

```text
your-project/.agents/skills/anime-badge-maker
```

## Usage examples

### Full two-image workflow

Upload one or more character or figure references:

```text
Make this according to the badge standard.
```

```text
按徽章标准制作。
```

### Artwork only

```text
Use $anime-badge-maker and create only the circular badge artwork.
```

### Physical mockup only

Upload a completed circular design and a physical badge photograph:

```text
Use $anime-badge-maker to replace only the printed face with this design.
```

### Use a custom physical badge photograph

Upload character references together with your badge photo:

```text
Create the badge art, then place the approved result into my physical badge photo.
```

## Decision priorities

The Skill uses this priority order:

1. Identity accuracy.
2. Anatomical and ownership correctness.
3. Preservation of expression, eye state, clothing, accessories, and key action.
4. Circular composition and subject prominence.
5. Background atmosphere and decorative polish.

A visually dramatic result must still be rejected if it changes the character or contains malformed or foreign limbs.

## Physical mockup invariants

The physical mockup stage does not reinterpret the character. It uses the approved artwork as the exact insert and changes only what is necessary to match the badge surface:

- perspective and curvature;
- crop at the printable boundary;
- photographic exposure and color temperature;
- highlights and reflections over the artwork;
- edge occlusion under the metal rim.

The result should look manufactured and photographed, not like a circular image pasted over a photo.

## Print-production note

Default outputs are high-resolution visual designs and product previews. They are not automatically production-ready print files. For manufacturing, provide the vendor's diameter, bleed, safe-area, resolution, and color-profile requirements.

## Privacy, copyright, and responsible use

- Only upload or distribute references you are allowed to use.
- Do not reproduce source watermarks, seller handles, studio marks, or platform overlays in generated artwork.
- This public repository intentionally excludes the historical anime source images and generated character examples used during private development.
- The included blank physical badge photograph was generated specifically for this open-source release and contains no characters, trademarks, or text.
- Users remain responsible for rights associated with the characters and reference material they process.

## Repository structure

```text
anime-badge-maker/
├── README.md
├── README.zh-CN.md
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
└── skills/
    └── anime-badge-maker/
        ├── SKILL.md
        ├── README.md
        ├── quality-checklist.md
        ├── agents/openai.yaml
        ├── assets/default-blank-badge.png
        └── references/
            ├── README.md
            └── design-rationale.md
```

## Contributing

Bug reports and pull requests are welcome. The most valuable reports include the input roles, expected invariant, observed failure, and whether the defect occurred in the artwork or mockup stage. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Released under the [MIT License](LICENSE).

## References

The Skill follows the open Agent Skills structure used by Codex. See the [official OpenAI documentation for building skills](https://learn.chatgpt.com/docs/build-skills).

