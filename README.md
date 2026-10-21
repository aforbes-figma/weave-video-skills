# Make your own little movies in Weave

I started playing with Weave to learn how to use it and ended up building myself a little production team.

These three skills help turn a rough idea into the prompts and references you need to make a video. They bring in filmmaking decisions—camera work, lighting, timing, character consistency—that I wouldn’t necessarily know to ask for.

You work through the idea in chat, then copy the prompts into Weave to generate the images and video. The skills produce prompts and guidance; you generate and assemble the media in Weave.

## Meet the production team

| Skill | What it does |
| --- | --- |
| **[Video Producer](skills/weave-video-producer/SKILL.md)** | Start here. Develop the concept, story, shots, camera moves, dialogue, and timing. Bring in the reference skills when needed. |
| **[Character Sheet Builder](skills/character-sheet-builder/SKILL.md)** | Define characters and wardrobe, then write prompts for references to help keep them consistent across shots. |
| **[Reference Maker](skills/reference-maker/SKILL.md)** | Plan locations, cars, props, and scene composition. Write prompts for useful references before adding motion. |

## Get started in Codex

You’ll need Codex, access to this private repository, and access to Weave and your chosen generation model.

1. Copy this repository’s GitHub URL.
2. In Codex, ask: “Use skill-installer to install all three skills from this repository: [paste the repository URL]. The folders are skills/weave-video-producer, skills/character-sheet-builder, and skills/reference-maker. Include all supporting files.”
3. Confirm that all three skills appear in your available skills. If they don’t appear, restart Codex.

These are complete skill folders, including the reference files they use. Downloading the repository or attaching a ZIP to a chat is not the same as installing the skills. Other assistants may support these files, but their setup steps differ; this guide covers Codex.

## Try this

> Use my weave-video-producer skill. I want to make a 10-second cinematic video of me racing through Tokyo at night. Help me work out the shots and references. I’ll generate everything in Weave.

## How I use them

1. **Start with an idea.** Describe what you want to make, the style, and anything you already have in mind.
2. **Work out the shots.** Go back and forth with the producer on what happens, how it’s filmed, and how much can fit into the clip.
3. **Build the references you need.** Generate the character, setting, and key compositions in Weave using the prompts from the skills. Get those looking right before moving on.
4. **Bring it together.** Connect the approved references in Weave and ask the producer for the final timed video prompt. Share the exact reference node names and connection order so it can map the inputs correctly.
5. **Generate and refine.** Bring the result back into chat and explain what needs changing. The skills return complete revised prompts you can paste back into Weave.

For a simple video, you can skip references and start with a text-only prompt. You don’t need the full production workflow every time.
