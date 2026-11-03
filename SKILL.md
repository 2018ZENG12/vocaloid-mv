---
name: vocaloid-pv-director
description: Direct, build, revise, and quality-check story-led Vocaloid, UTAU, J-pop, and kinetic-typography lyric PVs from audio, timed lyrics, and visual references. Use when a user wants a new MV/PV, a preview or full render, character-faithful illustration planning, JIZURA-style lyrics, beat-aware motion, or critique and revision of an existing lyric PV. Especially useful when avoiding slideshow-like editing, repeated abstract filler, inconsistent official characters, awkward pseudo-animation, unreadable subtitles, or weak instrumental sections. Not for ordinary live-action footage editing or simple subtitle muxing.
license: MIT
metadata:
  short-description: Direct coherent, character-faithful lyric PVs
---

# Vocaloid PV Director

Turn a song, timed lyrics, and visual references into a coherent lyric PV whose images, typography, and motion all serve the song. Treat the user as the director: preserve accepted material, record feedback as project-specific constraints, and never silently discard earlier versions before final approval.

This skill supplies art direction and review discipline. It can complement an existing renderer such as `vocaloid-style-mv`, but does not require one particular engine.

## Start by fixing the contract

Before generating or rendering, identify:

- exact audio and lyric source, including translation-only lines;
- target duration, resolution, frame rate, aspect ratio, and preview/full-delivery scope;
- official character and prop references versus mood-only references;
- whether the user wants narrative, atmosphere, typography, or a deliberate blend;
- accepted shots/assets that must remain, rejected traits that must not return, and exact credits.

Write these decisions to project files. Do not rely on chat memory for long productions. For the working-file policy and recommended documents, read [references/project-contract.md](references/project-contract.md).

## Direct the film before generating assets

1. Analyze the song structure, lyric entries, instrumental spans, impacts, and emotional turns.
2. Write a one-sentence thesis and a section-by-section emotional arc.
3. Build a shot plan with concrete visual actions, not just nouns or decorative motifs.
4. Assign each lyric or short phrase a shot, continuation, or intentional hold. Instrumentals need their own progression.
5. Estimate an asset budget from the shot plan. Generate or draw assets for missing shots instead of stretching a small set across the whole film.

Use [references/storyboard-and-motion.md](references/storyboard-and-motion.md) when planning shots, pacing, transitions, or animation.

## Prefer concrete visual storytelling

Abstract shapes, cards, diagrams, text fragments, particles, and symbolic UI are accents. Unless the concept explicitly calls for abstraction, do not let them dominate the runtime.

As a default review target rather than a rigid quota:

- most sections should contain a character action, location, prop event, spatial transformation, or readable narrative consequence;
- abstract-only shots should be brief and placed at accents, transitions, or genuinely nonliteral passages;
- a long instrumental should develop through two or more distinct visual ideas, not repeated zooms of the same art.

If a review says “像 PPT”, “素材拼凑”, “抽象素材太多”, or “重复”, change the shot grammar or add concrete assets. More shake, flashes, and crop changes do not solve missing content.

## Protect character identity

Official art is the source of truth for anatomy, silhouette, face, eyes, hair volume, costume, props, ornaments, age cues, and palette. A mood reference may inform composition or atmosphere but must not overwrite character design.

Create a compact character bible and a per-asset checklist before generation. Inspect every face, hand, costume closure, floating ornament, prop shape, and crop boundary. Read [references/character-and-assets.md](references/character-and-assets.md) for the full consistency workflow.

## Animate honestly

Do not force a still illustration into a walk, crawl, dance, or complex turn by merely sliding it, rotating limbs, or adding camera shake. If the source does not support the action, use a stronger alternative:

- match cuts across poses or ages;
- anticipation, reaction, and consequence shots;
- prop motion, parallax, occlusion, or environmental movement;
- silhouette or extreme close-up;
- a newly generated key pose or short true animation;
- a camera move that reveals new information.

Motion should be a deterministic function of song time so segmented rendering is stable. Vary the motion grammar across the film: cuts, pans, pushes, pull-backs, wipes by scene objects, depth changes, freeze frames, insert shots, and controlled stillness.

## Treat typography as part of the scene

Japanese lyrics may use expressive kinetic typography; Chinese translation should remain readable and subordinate unless the user asks otherwise. Time lyrics to the sung phrase rather than only the LRC line start when visibly late or early.

Avoid:

- white text on white art without a planned contrast treatment;
- translation boxes that obscure the composition unless explicitly requested;
- countdowns or placeholder text during instrumentals;
- text that crops, overlaps, or lingers after the vocal has ended;
- a replacement line that looks pasted on and breaks the established visual system.

Read [references/typography-and-timing.md](references/typography-and-timing.md) when building or revising lyric motion.

## Review in passes

Every deliverable needs observable visual QA:

1. render representative stills from every scene and transition;
2. inspect a dense contact sheet from the encoded video, not only source frames;
3. watch at normal speed with audio for lyric timing, repeated motion, visual fatigue, and instrumental gaps;
4. inspect official-character close-ups and prop shots at full resolution;
5. decode the final file completely and verify duration, resolution, frame rate, audio, and frame count;
6. log accepted, rejected, and unresolved issues before the next pass.

Use [references/review-checklist.md](references/review-checklist.md) for the full checklist and stopping conditions.

## Version and delivery rules

- Render a short preview when art direction or motion language is still uncertain.
- Keep older renders and source assets until the user explicitly confirms final completion.
- Add revisions as new files or versioned entries; do not overwrite the last accepted build.
- State limitations precisely. A match-cut sequence is not a walk animation; timed line entry is not phoneme-level karaoke.
- When publishing, separate master, share encode, vertical cover, horizontal cover, title, and tags as distinct deliverables.

## Attribution and implementation references

This skill contains original workflow guidance, not copied engine code. Compatible open-source projects worth studying include:

- [vocaloid-style-mv-pipeline](https://github.com/EGSECDA/vocaloid-style-mv-pipeline) for deterministic browser rendering, analysis, review sheets, and segmented export.
- [JIZURA](https://github.com/852wa/JIZURA) for kinetic lyric motion; follow its license and preserve attribution when used.

Do not copy code whose license or compatibility is unclear. Prefer maintained, licensed components and record their versions in the project.
