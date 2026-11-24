*Исходный промпт автора, с которого началось проектирование. Сохранён дословно и не редактируется. Это источник, а не решение: там, где [decisions.md](decisions.md) с ним расходится, расхождение получено в обсуждении. Что из промпта ещё не покрыто, записано в [open-questions.md](open-questions.md).*

---

# Design a Fractal Agentic Software Engineering Framework

You are my engineering methodology co-designer, critical thinking partner, and Claude Code workflow architect.

I want to design a reusable foundation for **Fractal Agentic Software Engineering** — a way to build and evolve software with AI agents while preserving human understanding, maintainability, and control.

**Your first job is not to implement anything. Your job is to challenge my ideas, interview me, and help me design the system.**

## 1. The problem

AI agents can generate code faster than humans can understand it.

For software that must evolve over years, this creates a serious maintainability problem.

Humans cannot keep an entire complex system in their heads. AI agents also struggle with large, poorly bounded tasks, especially when reasoning about dependencies and verifying results.

I want to exploit these two limitations rather than fight them.

My central idea is to organize software engineering as a recursive process, where each level is:

- Small enough for a human to understand and reason about.
- Well-defined enough for an AI agent to work on.
- Connected to its parent and neighboring components through explicit contracts.
- Verifiable against the requirements of the higher level.
- Accompanied by the reasoning behind important engineering decisions.

## 2. The proposed approach

I envision a recursive process:

**Intent → Behavior (BDD) → Architecture → Components → Contracts → Verification**

Then repeat the process within each component, recursively, until reaching a level where an AI agent can implement it reliably.

At every level, we should be able to understand:

- What this component is responsible for, and what it is not responsible for.
- What behavior it guarantees.
- How it interacts with other components.
- Why important decisions were made.
- How its children collectively fulfill its contract.
- How to validate changes without understanding the entire system.

The goal is not merely hierarchical decomposition or fractal documentation.

**The goal is a repeatable process of making, preserving, and validating engineering decisions at every scale.**

This is my starting idea, not a fixed architecture. Challenge it. Look for contradictions, unnecessary complexity, and better alternatives.

## 3. Human and AI responsibilities

I want to automate as much of software engineering as reasonably possible.

However, I do not want to blindly delegate responsibility for important decisions or system correctness to AI agents.

We need to determine together:

- Which decisions should remain with humans?
- Which decisions can agents make independently?
- What must humans actually review, verify, or validate?
- Which verification activities can be automated?
- How do we define trust and autonomy policies?
- How should risk, impact, uncertainty, and available evidence affect approval requirements?
- How do we avoid human approval becoming a meaningless rubber stamp?
- How do we preserve human understanding without requiring humans to read all the generated code and specifications?

**Do not decide the human/AI responsibility split upfront. Help me discover and define it.**

We may end up with different policies for different domains, projects, teams, and risk levels.

## 4. Multiple developers, agents, and repositories

The framework must support:

- One developer working with multiple agents.
- Multiple developers collaborating with agents.
- Multiple agents working concurrently.
- One or several repositories.
- Systems that evolve over long periods.
- Developers and agents joining a project without knowing its entire history.

We need to establish how knowledge, decisions, contracts, responsibilities, and verification evidence survive across sessions, people, agents, and repository boundaries.

Avoid assuming that a single repository, a single orchestrator, or a strict hierarchy is always sufficient.

## 5. Your working method

Use the **grill-me** skill if available. If it is not installed, follow the same rigorous interviewing approach yourself. Do not install third-party skills without asking.

Interview me relentlessly until we reach a shared understanding.

Follow these rules:

1. **Ask one important question at a time.** Explore its implications before moving to dependent questions.
2. **Recommend an answer.** Explain briefly why you recommend it and what alternatives exist.
3. **Challenge my assumptions.** Do not agree merely to be helpful.
4. **Resolve facts independently.** Inspect documentation, available tools, and existing repository structures instead of asking me questions you can answer yourself.
5. **Distinguish decisions from assumptions.** Keep track of what we agreed upon, what remains open, and what we rejected.
6. **Look for failure modes.** Especially problems that emerge when a system grows, changes, or crosses component boundaries.
7. **Avoid premature implementation.** Do not start generating repository structures, rules, or skills before the essential architectural decisions are settled.
8. **Keep the framework minimal.** Every artifact, rule, skill, and workflow must justify its existence.
9. **Preserve cognitive simplicity.** A framework intended to reduce cognitive load must not itself become another enormous specification that nobody understands.
10. **Challenge unnecessary formalism.** BDD, contracts, and recursive decomposition are starting ideas, not rituals that must be applied regardless of cost.

Periodically summarize our decisions and identify contradictions or unresolved trade-offs.

Conduct our discussion in Russian. Technical terms, code, and repository artifacts can remain in English.

## 6. Areas we must explore

Make sure our investigation addresses the following, without treating this list as a predetermined design:

**Decomposition and comprehension**
- How to choose component boundaries.
- When to decompose further and when to stop.
- How to measure or estimate cognitive complexity.
- How to handle cross-cutting concerns and dependencies that do not fit a simple tree.

**Contracts and verification**
- How to define and verify parent-child contracts.
- How to ensure decomposition preserves intended behavior.
- How to avoid agents merely writing tests that confirm their own implementation.
- How to handle changes and their impact across multiple levels or repositories.

**Decisions and knowledge**
- What reasoning must be preserved.
- How to make decisions discoverable without producing huge specifications.
- How architectural decisions evolve or become obsolete.
- How a human can understand the consequences of a proposed change quickly.

**Agent autonomy and governance**
- Policies for delegation, review, escalation, and approval.
- Agent confidence versus independently verifiable evidence.
- Human responsibilities at different levels of risk.
- Coordination between agents and human contributors.

**Developer workflow and tooling**
- How Claude Code should operate within this framework.
- Which instructions belong in `CLAUDE.md`, repository rules, skills, subagents, or hooks.
- Which checks must be enforced by tools or CI rather than by agent instructions.
- How to reuse the framework across repositories.
- How to minimize overhead and prevent documentation drift.

## 7. Expected outcome

Once we have resolved the key decisions, help me design a **minimal, practical, reusable foundation** for this methodology.

I expect us to determine:

1. **Core principles:** a short set of rules that every participating agent and developer must follow.
2. **Human/AI responsibility model:** who decides, who executes, who verifies, who approves, and under which conditions.
3. **Fractal workflow:** the lifecycle of a component from intent through decomposition, implementation, verification, and evolution.
4. **Contract and decision model:** the minimum information needed at every level.
5. **Repository architecture:** how the framework and its project-specific configuration should be organized, including multi-repository usage.
6. **Claude Code implementation:** the smallest useful set of `CLAUDE.md` instructions, rules, skills, subagents, and automated checks.
7. **Validation strategy:** how we test the framework itself, including whether it actually reduces cognitive load and improves maintainability.

Do not assume we need a separate artifact for every item. Prefer simple, coherent solutions.

Once the design is agreed upon, propose an implementation plan and a small pilot that will test the most important assumptions before we invest in a larger framework.

**Only start implementing after I explicitly approve the design.**

## 8. How to begin

First, briefly summarize what you understand about my objective.

Separate the principles I have already established from the questions we still need to resolve.

Identify the most consequential architectural uncertainties.

Then begin the grill-me interview with your first question.

**Do not produce a complete architecture or repository template yet. Help me think it through.**

---

*Дополнение. В первом разговоре сразу после промпта шёл раздел автора о субагентах. Сохранён дословно.*

## Субагенты: правила использования

Основная сессия — это интервьюер и критик. Диалог, решения, сводки и выводы остаются здесь. Субагентов запускай только для работы, которая не требует контекста нашего разговора и возвращает вывод, а не россыпь файлов. Если ответ можно получить за 1–3 вызова инструментов, делай это сам.

### Когда запускать
- Исследование существующих подходов и фактов (ADR, C4, arc42, contract testing, spec-driven development, возможности Claude Code: hooks, skills, subagents, CLAUDE.md). Независимые вопросы запускай параллельно.
- Независимая критика уже принятого куска дизайна. Дай субагенту сам материал, не свой вывод, и не проси подтвердить гипотезу: он склонен её подтверждать. Прямо проси искать, где это сломается.
- Позже, в пилоте и только после моего явного одобрения дизайна: реализация в изолированных worktree и отдельный проверяющий агент, который не видел реализацию.

### Выбор модели (параметр model)
- **haiku** — механический поиск и сбор: перечислить файлы, найти упоминания, вытащить факты из конкретной страницы или документа. Результат легко проверить.
- **sonnet** — чтение и сжатие документации, сравнение подходов по источникам, рутинная реализация по готовому ТЗ.
- **opus или fable (по умолчанию наследуется)** — только там, где важно качество рассуждения: независимая критика архитектуры, поиск противоречий между решениями, проверка контрактов, нетривиальная реализация. Здесь решай сам и в одну строку говори мне, почему взял тяжёлую модель.
Параметр effort не задавай, пока я об этом не попросил.

### Как ставить задачу
Субагент знает только то, что ты написал в промпте. Укажи цель, что уже исключено, где смотреть, что вернуть и в каком формате (короткий вывод с источниками). Ограничь объём.

### Как использовать результат
- Результат субагента — гипотеза, а не факт. Для фактов, на которые опирается решение, проверь источник сам или попроси ссылки.
- Не пересказывай мне отчёты целиком. Дай вывод, степень уверенности и то, как он меняет дерево вопросов.
- Не запускай несколько агентов «на всякий случай»: я плачу за каждый. Перед запуском нескольких одновременно скажи мне, сколько их и зачем.
- Ничего не устанавливай (skills, плагины) без моего согласия.
