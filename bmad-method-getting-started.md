
### The Core Philosophy: "Vibe CEO" and the Two-Phase Workflow

Before we start, it's crucial to understand the BMAD philosophy. You are the **"Vibe CEO"**. Your job is to provide the vision, make key decisions, and guide the overall direction. Your AI agents are your expert team, responsible for the detailed execution.

The method is split into two main phases, designed to leverage the strengths of different AI environments:

1.  **Phase 1: Planning & Design (Web UI or Powerful IDEs):** This phase focuses on high-level thinking, creativity, and documentation. It's best done in an environment with a large context window and powerful reasoning models (like the Gemini web UI, Claude's web UI, or a custom GPT). This is the most cost-effective way to generate large, comprehensive documents.
2.  **Phase 2: Execution & Development (IDE):** This phase is all about implementation. It's done in your local Integrated Development Environment (IDE) where agents have direct access to your file system to create, edit, and test code.

This entire guide is based on the standard workflow outlined in `bmad-core/workflows/greenfield-fullstack.yaml`.

-----

### Phase 1: Planning and Design (The "What" and "Why")

This phase is about creating the foundational documents that will guide the entire project.

#### Step 1: Install BMAD Method in Your New Project

First, create a new, empty folder for your project and install the BMAD Method. This sets up the core agent definitions and tools.

```bash
# Create your project folder
mkdir my-new-game && cd my-new-game

# Run the interactive installer
npx bmad-method install
```

When prompted, you can select the IDEs you plan to use (like GitHub Copilot, Claude Code, etc.). This command creates a hidden `.bmad-core` directory in your project, which is the "brain" containing all the agent instructions.

#### Step 2: Ideation and Project Brief (Role: Analyst)

Every great project starts with a clear idea. The **Analyst** agent helps you solidify this.

  * **What you do:** You provide the initial spark—a basic idea for your application.
  * **What the Analyst does:** It facilitates brainstorming, performs market/competitor research (optional), and synthesizes everything into a **Project Brief**. This brief is the foundational document that defines the problem, the proposed solution, the target users, and the MVP scope.
  * **Why it's important:** A solid brief ensures everyone (including future AI agents) is aligned on the project's core purpose before any major work begins.

**How to do it:**

  * **In a Web UI (Gemini/Claude):** Upload the `team-fullstack.txt` bundle to create your team. Start a conversation with the orchestrator and ask to switch to the Analyst.
  * **In your IDE:** Invoke the `analyst` agent and ask it to help you `create-project-brief` using the `project-brief-tmpl.yaml`.

#### Step 3: Create the Product Requirements Document (PRD) (Role: Product Manager)

The **Product Manager (PM)** agent takes the Project Brief and expands it into a detailed **Product Requirements Document (PRD)**.

  * **What the PM does:** It defines all functional and non-functional requirements, establishes technical assumptions, and, most importantly, breaks the project down into **Epics** and **Stories**. This is the master plan for what will be built.
  * **Why it's important:** The PRD is the single source of truth for the project's requirements. The epics and stories created here will be implemented one-by-one in the development phase.

**How to do it:**
Invoke the `pm` agent and ask it to create a PRD based on the Project Brief. It will use the `prd-tmpl.yaml` and guide you through the process.

#### Step 4: Define the User Experience (Role: UX Expert)

If your project has a user interface, the **UX Expert** agent designs the user-facing aspects.

  * **What the UX Expert does:** It creates a `front-end-spec.md` that outlines user flows, information architecture, and core UI components. As an optional but highly recommended step, it can also generate a prompt for an AI UI generation tool (like Vercel's v0 or Lovable.ai) to quickly scaffold the frontend.
  * **Why it's important:** This ensures the user experience is considered from the start and provides a clear guide for the frontend implementation.

**How to do it:**
Invoke the `ux-expert` agent. Provide the PRD as context and ask it to create a `front-end-spec`.

#### Step 5: Design the Technical Architecture (Role: Architect)

The **Architect** agent creates the technical blueprint for the entire application.

  * **What the Architect does:** Using the PRD and UX Spec as input, it creates the `architecture.md` document. This file defines the tech stack, database schema, API specifications, project structure, and coding standards.
  * **Why it's important:** This document provides the "rules of the road" for the development agents. It ensures that the code they write is consistent, scalable, and follows best practices.

**How to do it:**
Invoke the `architect` agent, provide the PRD and UX spec, and ask it to create the architecture document using the `fullstack-architecture-tmpl.yaml`.

#### Step 6: Validate and Align (Role: Product Owner)

The **Product Owner (PO)** is the final gatekeeper of the planning phase.

  * **What the PO does:** It runs the `po-master-checklist` to ensure all documents (Brief, PRD, Arch) are consistent, complete, and logically sound. If it finds discrepancies, it will suggest updates.
  * **Why it's important:** This crucial validation step catches errors and misalignments *before* development starts, saving significant time and rework.

**How to do it:**
Invoke the `po` agent and ask it to validate all the planning artifacts.

-----

### The Great Transition: From Planning to Execution

You now have your master plans: `prd.md` and `architecture.md`.

**You must now move from the web UI into your local IDE.**

1.  **Save Your Documents:** Copy the final `prd.md` and `architecture.md` files into a `docs/` directory inside your local project folder.
2.  **Open Your Project in Your IDE:** Open the project folder in VS Code (with Copilot), Zed (with Claude Code), etc.

-----

### Phase 2: Execution and Development (The "How")

This phase happens entirely in your IDE, where agents can read and write files.

#### Step 7: Shard the Documents (Role: Product Owner)

Large documents are difficult for AI agents to process efficiently in an IDE. **Sharding** breaks them into smaller, context-rich pieces.

  * **What the PO does:** It uses the `shard-doc` task to split `prd.md` into individual epic files and `architecture.md` into component files (e.g., `coding-standards.md`, `tech-stack.md`).
  * **Why it's important:** This allows the development agents to load *only* the specific context they need for a single task, dramatically improving performance and accuracy.

**How to do it:**
In your IDE, invoke the `po` agent and give it the following commands, one at a time:
`*shard-doc docs/prd.md prd`
`*shard-doc docs/architecture.md architecture`

#### Step 8: The Core Development Loop

This is the heart of the BMAD execution phase. You will repeat this cycle for every story in your PRD. **It is critical to start a new, clean chat session for each agent handoff** to prevent context bleed and keep the agents focused.

**8a. Story Creation (Role: Scrum Master)**

  * **Start a NEW CHAT.**
  * Invoke the `sm` (Scrum Master) agent.
  * Run the `*draft` command.
  * The SM will read the sharded epic and architecture files and create the next logical story. This story file is hyper-detailed, containing everything the dev agent needs: acceptance criteria, file paths, coding standards, and technical notes, all sourced from your planning documents.

**8b. Your Review**

  * Review the generated story file in `docs/stories/`. It will be in `Draft` status.
  * If it looks good, change the status to `Approved`. You are the "Vibe CEO" giving the green light.

**8c. Implementation (Role: Developer)**

  * **Start a NEW, CLEAN CHAT.**
  * Invoke the `dev` (Developer) agent.
  * Tell it which story to implement (e.g., `develop story 1.1`).
  * The Dev agent will read the story, implement the code, write tests, and update the story file to mark tasks as complete. When finished, it sets the story status to `Review`.

**8d. Quality Assurance (Role: QA Agent)**

  * **Start a NEW, CLEAN CHAT.**
  * Invoke the `qa` agent.
  * Run the `*review {story-file}` command.
  * The QA agent acts as a senior developer, reviewing the code for quality, adherence to standards, and potential bugs. It can even perform refactoring. When done, it will recommend a final status (`Done` or back to `InProgress`).

**8e. Repeat**

  * Once a story is `Done`, you go back to step 8a to create the next one. Continue this loop until all stories for the project are complete.

-----

### Tool-Specific Invocation Guide

Here’s how to invoke the agents in the tools you mentioned:

#### **GitHub Copilot (in VS Code) / Trae**

These tools use the `@` mention syntax. The BMAD installer configures this for you.

```
# In the Copilot Chat window:
@sm *draft
@dev implement story 1.2
```

#### **Claude Code / Windsurf**

These tools typically use the `/` slash command syntax.

```
# In the AI chat window:
/sm *draft
/dev implement story 1.2
```

#### **Gemini CLI**

This is the most manual process, as the CLI cannot automatically discover agents. You must provide the agent's definition as context for every command.

1.  **Copy the Agent's Content:**
    ```bash
    # On macOS
    cat .bmad-core/agents/sm.md | pbcopy

    # On Windows (in PowerShell)
    Get-Content .bmad-core\agents\sm.md | Set-Clipboard
    ```
2.  **Run the Gemini CLI:**
    ```bash
    gemini "
    <PASTE THE AGENT CONTENT HERE>

    Now, following the instructions above, execute the *draft command.
    "
    ```
    You must repeat this process of providing the agent context for every interaction.

#### **Codex**

The `docs/user-guide.md` file specifies that Codex integration relies on the `AGENTS.md` file that the installer creates.

1.  **Installation:** Ensure you selected `Codex` during the `npx bmad-method install` process.
2.  **Invocation:** You would use the `codex` CLI tool, which is designed to read the `AGENTS.md` file as its primary source of agent context.
    ```bash
    # In your project root
    codex "As the Scrum Master, draft the next story."
    ```

By following this comprehensive workflow, you can leverage the BMAD Method to systematically take a project from a simple idea to a fully implemented application, using a structured, repeatable, and high-quality process.
