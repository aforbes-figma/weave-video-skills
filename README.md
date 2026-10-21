# Figma Weave - Video Production Toolkit

Video production skills that help you turn rough ideas into the prompts and references you need to make high quality videos in Figma Weave. The three skills work together to guide story development, camera work, lighting, timing, and character consistency. Work through an idea in chat, then copy the prompts into Weave to generate and assemble the images and video.

## Meet the production team

| Skill | What it does |
| --- | --- |
| **[Video Producer](skills/weave-video-producer/SKILL.md)** | Start here. Develop the concept, story, shots, camera moves, dialogue, and timing. Bring in the reference skills when needed. |
| **[Character Sheet Builder](skills/character-sheet-builder/SKILL.md)** | Define characters and wardrobe, then write prompts for references to help keep them consistent across shots. |
| **[Reference Maker](skills/reference-maker/SKILL.md)** | Plan locations, cars, props, and scene composition. Write prompts for useful references before adding motion. |

## Using the skills

Install all three skills in an assistant that supports skills, then start with Video Producer. You’ll also need access to Figma Weave and your chosen generation model.

- **Download the files:** Choose **Code → Download ZIP** on this repository, unzip it, and follow your assistant’s instructions for installing the three folders inside `skills/`. Include each folder’s supporting files.
- **Use a skill installer:** Point your assistant’s installer to this repository and ask it to install all three skills. For example:

> Install weave-video-producer, character-sheet-builder, and reference-maker from https://github.com/aforbes-figma/weave-video-skills. They’re in the skills/ directory. Include all supporting reference files.

Installation steps vary by assistant. Once installed, you can call a skill by name or describe what you want to make.

## Try this

**A cinematic action clip**

> Use my weave-video-producer skill. I want to make a 10-second cinematic video of me racing through Tokyo at night. Help me work out the shots and references. I’ll generate everything in Weave.

**A simple clip without references**

> Use my weave-video-producer skill. Help me plan an 8-second video of a tiny robot trying to carry an oversized coffee across a desk. Keep it playful, with two shots and no dialogue. Start with a text-only prompt I can run in Weave.

## What each skill does

### Video Producer

Turns a rough idea into a production plan: what happens, how the shots connect, where the camera moves, and how the action and dialogue fit the runtime. It helps choose between a simple text-only approach and a workflow built around references, then brings in the other skills when needed.

The output is a copy-ready video prompt adapted to the chosen model, with timing, camera direction, performance, audio guidance, and reference mappings where relevant. If a result needs work, bring it back for review and a complete revised prompt.

### Character Sheet Builder

Helps define a character’s appearance, proportions, wardrobe, and the details that need to stay consistent. It can work from a description or supplied photos and guides decisions that affect the planned shots.

It writes prompts for character sheets and focused references, such as a face, outfit, or expression. Each reference has a clear job, so the video model has fewer competing details to interpret. It also helps diagnose and repair character drift between generations.

### Reference Maker

Plans the visual building blocks around the character: locations, products, props, lighting, composition, and key starting or ending frames. It can place an approved character into a scene while preserving the character reference’s identity and wardrobe.

It writes prompts for the smallest useful set of reference images, explains what each image controls, and gives them stable Weave node names. The aim is to get the scene and composition right before spending time on motion.

## How it works

1. **Start with an idea.** Describe what you want to make, the style, and anything you already have in mind.
2. **Work out the shots.** Go back and forth with the producer on what happens, how it’s filmed, and how much can fit into the clip.
3. **Build the references you need.** Generate the character, setting, and key compositions in Weave using the prompts from the skills. Get those looking right before moving on.
4. **Bring it together.** Connect the approved references in Weave and ask the producer for the final timed video prompt. Share the exact reference node names and connection order so it can map the inputs correctly.
5. **Generate and refine.** Bring the result back into chat and explain what needs changing. The skills return complete revised prompts you can paste back into Weave.

For a simple video, you can skip references and start with a text-only prompt. You don’t need the full production workflow every time.

## Getting better results

| Topic | What to share or consider |
| --- | --- |
| **Your starting brief** | Describe the idea, target model, duration, aspect ratio, and any images, clips, or other assets you already have. If you’re unsure about a choice, ask the producer to help work it out. |
| **Your starting point** | Start from text for a quick concept, animate an existing first frame, or build a workflow using references for characters, locations, and props. The producer can help choose the approach based on your goal and the inputs available in your Weave node. |
| **What needs to stay consistent** | Explain which details must stay exact, which are preferences, and which the skills can explore. These might include a character’s face, wardrobe, product shape, dialogue, or scene layout. |
| **Finishing details** | For exact logos, typography, or product UI, plan to use supplied assets or add them in a compositing pass. Include those requirements early so the shots leave room for them. |
