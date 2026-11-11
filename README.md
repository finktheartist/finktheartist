# Justin Finkelman

I build agent systems that can be left alone with real work, and interface parts you want to touch.

By day I am a Senior AI Engineer at [Addition](https://addition.ml), building demos and prototypes that explain agentic AI to people who have not met it yet. Before that: illustration, game art, and ten years running a screen printing studio, which is where I learned that nothing is finished until somebody else can use it on a deadline.

[Portfolio](https://finktheartist.tech) · [Substack](https://finktheartist.substack.com) · [LinkedIn](https://www.linkedin.com/in/justin-finkelman/) · [Email](mailto:finktheartist@gmail.com)

---

## How I run agents

I run four agents across two machines: Claude Code, Codex, Gemini, and Hermes, an agent I built that lives on a rented server and talks to me over Telegram. They share a job ledger and a memory. Since July the ledger has taken more than two thousand jobs.

Making the agents smarter was never the hard part. These are the rules that were.

- **Permission lives below the model.** Every job carries named capabilities: read, write, network, send, deploy, publish, spend, destructive. An agent checks the ledger before a sensitive action, and a denial means stop and ask me. The model does not get a vote on its own permissions.
- **A yes is for exact bytes.** Anything that reaches a person or a public page is approved as a sha256 of the final file, and the approval works once. Change a comma after I say yes and the yes is gone. This README was published that way.
- **Files, not a database.** A job is one JSON file with an append-only event log beside it. The ledger syncs between machines, and a shared SQLite file would not survive that.
- **One memory, and I am the editor.** What one agent learns goes into a shared store as a candidate. The others only get it after I decide it is worth keeping.
- **One message a day.** The whole fleet gets a single digest at eight in the morning, and every line in it is a decision I can make from my phone. When nothing needs me, the script prints `[SILENT]` and no message is sent. That string is my favorite feature.
- **Work happens where I can see it.** Agents run in visible terminal panes, not headless in the background.

The system itself is private, and its safety rules have their own test suite. The same approach shows up in the public work below, starting with a repo that ships the agent skill it was made with.

## Pixel Worlds

**[Repo](https://github.com/finktheartist/pixel-worlds) · [Live gallery](https://pixel-worlds.vercel.app)**

Ordinary controls with a small living pixel-art scene inside them. The password field builds a castle as you type, and a stronger password gets more castle. The delete button has a dragon asleep in it. Hold the button and the fire is the fill. The agent status line is a wizard at his desk doing whatever the agent is doing, including failing.

Six components, one file each. Everything is painted in code: no image files, no dependencies, no network requests.

```sh
npx shadcn add finktheartist/pixel-worlds/hoard
```

It is built for agents as much as for people. An `llms.txt` lists every file, each component has a button that copies a prompt for your coding agent, and the repo ships the skill the six were made with, so your agent can make a seventh. It will get a reasonable first pass. Mine took many rounds of looking at frames and fixing them, and yours will too.

## Things you can pick up

<table>
<tr>
<td width="33%" valign="top">
<a href="https://swatch-rack.vercel.app"><img src="https://raw.githubusercontent.com/finktheartist/swatch-rack/main/docs/demo.gif" alt="Swatch Rack: browsing a rack of paper color cards and generating a palette"></a>
<br><br>
<b><a href="https://github.com/finktheartist/swatch-rack">Swatch Rack</a></b>
<br>
A rack of paper color cards you browse, not a grid you scan. Pick up to three and it suggests palettes matched in OKLCH against the catalog, so every suggested color is a card that exists.
</td>
<td width="33%" valign="top">
<a href="https://book-shelf-mu-bice.vercel.app"><img src="https://raw.githubusercontent.com/finktheartist/book-shelf/main/docs/demo.gif" alt="Book Shelf: pulling a hardback off a 3D shelf and opening it"></a>
<br><br>
<b><a href="https://github.com/finktheartist/book-shelf">Book Shelf</a></b>
<br>
A bookcase of hardbacks where every binding is generated from the title and author alone. No cover art, nothing to license. A series shares a binding, the way a real run does.
</td>
<td width="33%" valign="top">
<a href="https://bubble-wrap-simulator.vercel.app"><img src="https://raw.githubusercontent.com/finktheartist/bubble-wrap-simulator/main/docs/gameplay-poster.jpg" alt="Bubble Wrap Simulator: a first person room made of bubble wrap"></a>
<br><br>
<b><a href="https://github.com/finktheartist/bubble-wrap-simulator">Bubble Wrap Simulator</a></b>
<br>
A first person room with more than 43,000 bubbles and nine tools for popping them. One of the tools is a bowling cannon. React, Three.js, Rapier physics.
</td>
</tr>
</table>

Swatch Rack and Book Shelf are single Web Components. All three run in the browser with nothing to install.

## Write-ups

Most of the agent work lives in private repos, so these link to case studies instead of code.

- **[Glyph Agent](https://finktheartist.tech/glyph-personal-agent)**. Where the fleet started: a persistent agent on a server with cross-session memory, scheduled briefings, and Telegram as its only interface.
- **[From Sketch to 3D](https://finktheartist.tech/sketchbook-ml-to-3d)**. Sketchbook drawings become rigged, walking 3D characters in a browser. A model judges each stage against a written rubric and refuses to spend money when it predicts a defect.
- **[Monodoro](https://finktheartist.tech/monodoro)**. A focus timer with a habit loop. My first iOS app.

I also write about how these get built, including the parts that went badly. Start with [I asked a model to find a dog. It gave me six chairs.](https://finktheartist.substack.com/p/i-asked-a-model-to-find-a-dog-it)

---

Chicago area. If something here is broken, open an issue on that repo. I would like to know.
