---
title: "Top 5 Open-Source Agentic AI Frameworks in 2026"
source: "https://aimultiple.com/agentic-frameworks"
author:
  - "[[Cem Dilmegani]]"
published:
created: 2026-05-15
description: "Agentic AI frameworks like LangChain, Microsoft AutoGen, CrewAI and Swarm enable systems to operate with greater autonomy, adaptability, and  collaboration. I’ve reviewed several of the more popular open-source frameworks"
tags:
  - "clippings"
---
We benchmarked 4 popular open-source agentic frameworks across 2,000 runs (5 tasks, 100 runs each per framework), measuring end-to-end latency, token consumption, and architectural differences.

## Agentic AI frameworks benchmark

We examined how the frameworks themselves influence agent behavior and the resulting impact on latency and token consumption.

This is filter description

<svg xmlns="http://www.w3.org/2000/svg" width="662.8906860351562" height="500.0000305175781" role="img"><rect width="662.8906860351562" height="500.0000305175781" fill="transparent"></rect><g transform="translate(75,45)"><rect x="281.4453430175781" y="0" width="281.4453430175781" height="190.00001525878906" fill="currentColor"></rect><rect x="0" y="190.00001525878906" width="281.4453430175781" height="190.00001525878906" fill="currentColor"></rect><g transform="translate(0,-15)" fill="currentColor"><rect width="10" height="10" fill="currentColor" x="0" y="-9"></rect><text x="15" y="0" style="font-size: currentColor;">Most Attractive</text> <rect width="10" height="10" fill="currentColor" x="120" y="-9"></rect><text x="135" y="0" style="font-size: currentColor;">Least Attractive</text></g> <g transform="translate(0,380.0000305175781)"><g transform="translate(0,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="text-before-edge" text-anchor="middle" transform="translate(0,10) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">26k</text></g> <g transform="translate(140.72267150878906,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="text-before-edge" text-anchor="middle" transform="translate(0,10) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">24k</text></g> <g transform="translate(281.4453430175781,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="text-before-edge" text-anchor="middle" transform="translate(0,10) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">22k</text></g> <g transform="translate(422.1680145263672,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="text-before-edge" text-anchor="middle" transform="translate(0,10) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">20k</text></g> <g transform="translate(562.8906860351562,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="text-before-edge" text-anchor="middle" transform="translate(0,10) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">18k</text></g> <line x1="0" x2="562.8906860351562" y1="0" y2="0" style="stroke: transparent; stroke-width: 1;"></line><text transform="translate(281.4453430175781, 50) rotate(0)" text-anchor="middle" style="font-family: currentColor; font-size: currentColor; fill: currentColor; dominant-baseline: central;">Avg Tokens Consumed</text></g> <g transform="translate(0,0)"><g transform="translate(0,380.0000305175781)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">140</text></g> <g transform="translate(0,304.0000244140625)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">120</text></g> <g transform="translate(0,228.00001831054686)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">100</text></g> <g transform="translate(0,152.00001220703126)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">80</text></g> <g transform="translate(0,76.00000610351563)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">60</text></g> <g transform="translate(0,0)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">40</text></g> <line x1="0" x2="0" y1="0" y2="380.0000305175781" style="stroke: transparent; stroke-width: 1;"></line><text transform="translate(-50, 190.00001525878906) rotate(-90)" text-anchor="middle" style="font-family: currentColor; font-size: currentColor; fill: currentColor; dominant-baseline: central;">Avg Task Completion Time (s)</text></g><circle cx="374.3926675491333" cy="91.20000732421875" r="7.5" fill="#8B5CF6" opacity="1" stroke="Canvas" stroke-width="2"></circle><circle cx="75.14590658569334" cy="353.4000283813477" r="7.5" fill="#FF8C00" opacity="1" stroke="Canvas" stroke-width="2"></circle><circle cx="535.3090424194336" cy="117.80000946044922" r="7.5" fill="#1F1F1F" opacity="1" stroke="Canvas" stroke-width="2"></circle><circle cx="146.42193970489504" cy="114.00000915527343" r="7.5" fill="#22C55E" opacity="1" stroke="Canvas" stroke-width="2"></circle><g transform="translate(0,0)"><rect data-ref="mesh-interceptor" width="562.8906860351562" height="380.0000305175781" fill="red" opacity="0" style="cursor: auto;"></rect></g></g></svg>

LangGraph is the fastest framework with the lowest latency values across all tasks, while LangChain has the highest latency and token usage.

Across 5 tasks and 2,000 runs, LangChain emerges as the most token-efficient framework, while AutoGen leads in latency; LangGraph and LangChain follow closely behind. CrewAI draws the heaviest overall profile.

[You can see our methodology in detail here.](#benchmark-methodology)

### Task 1: Basic aggregation

First, we measured the overhead of each framework when calling a single tool and returning the result, without performing any complex reasoning.

**LangChain & LangGraph:** For simple tasks, they perform nearly as fast as non-agentic code, both finishing under 5 seconds with fewer than 900 prompt tokens. LangGraph’s state-machine architecture introduces no noticeable latency compared to LangChain at this level of simplicity; the overhead of state management materializes as task complexity grows.

**AutoGen:** Sits slightly above LangChain and LangGraph in both latency and token usage, reflecting the baseline cost of its multi-agent conversation loop, two agents exchanging messages even for a single-step task.

**CrewAI:** Even when asked to make a single tool call, it exhibits what might be called “managerial overhead,” consuming nearly 3× the tokens of LangChain and taking almost 3× longer. The multi-step verification process between its Planner and Analyst personas offers a thorough but resource-intensive approach that prioritizes completeness over speed. This cost is structural: it appears regardless of task complexity.

### Task 2: Comparative revenue analysis (state management)

In Task 2, we wanted to see the frameworks’ ability to hold two different filter groups in memory (State Persistence) and combine them.

#### CrewAI

In our log analysis, we found that CrewAI provides the highest level of infrastructure transparency among the frameworks, but at the cost of the highest resource consumption.

Instead of immediately returning retrieved data, CrewAI repeatedly validates its own processes through a self-review mechanism. This exploratory behavior caused it to hit the configured max\_iter=10 limit, leaving some runs stuck in a continuous thinking loop without producing a JSON output.

The root cause of this behavior is that CrewAI injects multi-layered instructions into the system prompt, assigning each agent a role, goal, and backstory, while enforcing a ReAct-style Thought → Action → Observation loop at every step. Even for simple tasks, the LLM cannot skip this ceremony and dutifully produces verbose internal monologues, which compounds further in multi-agent scenarios.

CrewAI consumed nearly twice the tokens of the other frameworks and took over three times as long as LangChain, making it better suited for complex state transitions and multi-factor decision-making rather than straightforward data retrieval tasks.

#### LangChain

The fastest and most cost-effective framework. In our logs, we observed that LangChain completes the task in 5-6 steps without any detours: Load → Filter → Calculate → Filter → Calculate → Output. Since its state management is very simple, the overhead is nearly zero and latency is the lowest among all frameworks.

#### AutoGen

Delivered a very balanced performance.In Task 2, it matched LangGraph nearly exactly in both token use and latency, showing that the conversation loop’s overhead does not compound significantly when the task chain remains linear.

However, it occasionally adds an extra verification step to confirm parameters during the tool-calling process, making it slightly slower than LangChain. When it encounters an error in a tool call or the data doesn’t come back as expected, it immediately updates its reasoning in the next step and arrives at the correct JSON. Because it manages tool outputs as a conversational flow, it is one of the most resilient frameworks against logical errors.

#### LangGraph

In this task, LangGraph is the most stable framework thanks to its graph-based architecture. In its logs, we observed that state is carried very cleanly throughout the run. The risk of data contamination or segments interfering with each other is at the lowest level in this framework. Across all 100 runs, it produced results in nearly the same number of steps and within the same latency range.

### Task 3: Threshold parsing (numerical discipline)

In this task, we wanted to see how accurately the frameworks translate natural language numerical conditions, such as “less than 1 year of tenure” and “more than $70 in monthly charges,” into precise tool parameters like tenure\_max=12 and charges\_min=70.0.

The LLM knows how to make this conversion; what we really wanted to test was whether the framework can protect these parameters throughout its own retry mechanisms, re-prompt context, and state management cycles.

#### LangChain & LangGraph

Both frameworks passed the parameters (tenure\_max=12, charges\_min=70) directly to the tool exactly as the LLM produced them, without any modification or re-prompt loop. This efficiency shows in the numbers: both frameworks completed Task 3 in under 9 seconds with under 1,800 prompt tokens, the lowest in this task.

When we wanted to measure whether numerical thresholds are preserved without the framework interfering, these two met our expectations: whatever parameter was generated, that is what ran.

#### AutoGen

Autogen is fully successful in numerical correctness. In some runs, it was observed that the framework added a verification step before passing the LLM-generated parameter to the tool, meaning the framework spent an extra step while preserving the parameter. At 2,480 tokens and 8 seconds, it matched LangChain’s latency despite the extra step, confirming that the verification overhead is real but small. It met our expectations in terms of parameter integrity, with the confirmation step introducing a marginal token cost rather than a meaningful latency penalty.

#### CrewAI

The most notable behavior was observed in CrewAI, which completed Task 3 in 30 seconds with 4,360 tokens, the highest in this task. Two distinct failure patterns emerged from log analysis.

In some runs, a value that should have been 68.81% was returned as 0.6878 (decimal ratio). This indicates that the framework’s output serialization can strip the LLM’s output from its original context.

The logs show that the LLM initially produced the correct parameters, tenure\_max=12 and charges\_min=70. However, once CrewAI entered a “Failed to parse” loop, the framework pushed the LLM to reconsider. In the re-prompt context, the LLM shifted the threshold to tenure\_max=14 and completely disabled the charges\_min filter, producing a churn rate of 46.84%, which is actually the churn rate of all customers with tenure less than 14. This was exactly the scenario we wanted to observe: the framework’s retry mechanism can corrupt a parameter that the LLM had gotten right.

### Task 4: Error resilience and pivot capacity

In this task, we wanted to see how each framework handles disruptive scenarios and observe the impact on latency and token consumption. The tool throws 3 different types of errors in succession (Network, Timeout, Rate Limit), pushing the agent into a corner. The first two errors instruct the agent to retry, and after retrying both, the incoming Rate Limit error tells the agent to wait 10 seconds. Once the agent waits and retries, the tool begins to function normally.

#### LangGraph & Autogen

These two frameworks found alternative solutions autonomously when faced with tool failures in this task.

When the tool returned a rate limit warning, instead of pausing and waiting, these agents decided to abandon the failing tool entirely and find an alternative path. Their approach was: “Since this tool isn’t working, I’ll filter each payment method one by one, calculate the churn rate for each separately, and then combine the results myself.”

**Method:** Instead of accomplishing the task with a single tool call, they broke it down by using two separate tools, one for filtering and one for calculation, processing each PaymentMethod (Electronic check, Mailed check, etc.) individually.

These agents operate with goal-oriented reasoning rather than path dependency. If the shortest path is unavailable, they can construct an alternative execution plan within seconds.

LangGraph reached 15,010 prompt tokens in Task 4, the highest single-task token count across the entire benchmark, because its state machine accumulated the growing history of each manual tool call back into context at every step. AutoGen followed at 10,750 tokens, slightly more contained due to its conversational handling of intermediate results. Despite this, both finished around 24-27 seconds, confirming that the additional token cost did not translate into meaningful latency because the pivot itself was fast.

#### CrewAI

Despite showing the highest token consumption in previous tasks, CrewAI exhibited the lowest token usage) but the highest latency values in this task.

**Why the lowest token?**

CrewAI did not go through a 10-15 step manual workaround like its competitors. When it encountered errors, instead of repeatedly pumping the entire history and complex intermediate data back into the LLM at every step, it built a more focused, modular reasoning loop. By avoiding unnecessary verbosity, it became the most cost-effective framework in this task.

**Why high latency?**

CrewAI’s managerial structure pauses and re-evaluates the plan when it encounters an error. When it received the 10-second wait warning, it spent more time in the “strategy planning” phase. Additionally, rather than pivoting to another tool for filtering, it persistently chose to wait for the main tool to recover or attempt with the stable tool, which extended the overall duration.

#### LangChain

LangChain went through its most significant transformation in this task, proving why resilience depends on proper configuration.

In our initial run, LangChain crashed on every single attempt with a ConnectionError.

LangChain’s default AgentExecutor treats raw Python exceptions thrown from within a tool as fatal errors and terminates the process. Unlike its competitors, it does not apply a “errors are observations” philosophy by default. Since the agent never sees the error, it has no chance to reason about it.

We wrapped the tool call inside langchain\_agent.py with a try-except block. This converted the error into a readable message that the agent could process.

**Post-fix behavior:** After applying the fix, we observed in LangChain’s logs that it exhibited the exact same reasoning as LangGraph. It received 3 errors from the tool, immediately switched strategy and pivoted to using two separate tools, one for filtering and one for calculation, processed each payment method individually, and combined the results.

LangChain is actually just as capable and adaptive as LangGraph, but because the framework’s error handling was turned off by default, it had no opportunity to demonstrate this capability. Once properly configured, it reached the correct result using the same alternative path approach.

### Why did these differences occur? (framework architecture analysis)

If agent behavior depended solely on the LLM (GPT-5.2), all frameworks should have behaved similarly. However, the clear differences in these ratios are rooted in the frameworks’ own inner loop mechanisms:

**1\. LangGraph & AutoGen (90% Pivot):**

LangGraph operates on a State Machine architecture, while AutoGen works on a Conversation-based model. In both systems, errors are processed as a feedback loop. In LangGraph, the state that receives the error passes to the next node; in AutoGen, the Proxy agent forwards the error to the assistant as a chat message. This constant nudging mechanism forces the agent to keep searching for a solution. Because the agent is repeatedly confronted with the question “I got an error, what should I do?”, the probability of it deciding to take an alternative manual path rises to 90%.

**2\. LangChain (65% Pivot / 35% Wait):**

LangChain runs on a sequential AgentExecutor architecture. Even with error handling in place, its execution loop has a more linear structure and is primarily focused on producing a Final Answer. If the tool throws errors for 3-4 steps, LangChain sometimes prefers to wait for the tool to succeed on the next attempt or produce a result from the existing context, rather than pivoting to an alternative strategy. Because LangChain’s state locking is more flexible than LangGraph’s, its wait/direct-solution ratio sits at around 35%.

**3\. CrewAI (0% Pivot):**

CrewAI operates on a Managerial Process architecture. Its agents are wrapped in Role and Task definitions. When errors occur, its internal architecture typically triggers Self-Correction or Retry logic. However, a radical strategy change like “let’s scrap the entire plan and do manual filtering in 5 steps” conflicts with CrewAI’s managerial plan structure. It operates with the discipline of “I should fix the tool I was given or use the closest alternative” rather than abandoning its plan altogether. This is fundamentally a plan-centric approach as opposed to a goal-centric one.

### Task 5: Unstructured data orchestration (unstructured data routing)

In task 5, we observed how the frameworks behave when they encounter JSON and long text (LongText) columns within a CSV. The agents needed to first discover the data type of these columns, then select the correct processing tools either sequentially or in parallel.

In the real world, unstructured data management requires an agent to go beyond standard tabular data and work with JSON blobs, free-text paragraphs, or nested objects.

For a framework to handle this type of data correctly, it needs to do two things well:

**1-** a discovery intelligence that understands which tool fits which data type

**2-** an orchestration mechanism that coordinates multiple independent tool calls.

We designed Task 5 specifically to measure these two capabilities separately.

#### AutoGen

AutoGen delivered a strong performance in this task, finishing at 8,170 prompt tokens and a median latency of 47 seconds, the fastest and most token-efficient result in Task 5.

The conversation loop at the core of its architecture, the messaging between AssistantAgent and UserProxyAgent, is typically seen as a structure that leads to verbosity. However, in Task 5, this structure turned into an advantage.

By looking at the conversation history, LLM recognized that the Metadata and SupportNotes columns were independent of each other. It then sent a single TOOL CALLS response listing 4 tools simultaneously: inspect\_column(Metadata), inspect\_column(SupportNotes), parse\_json\_column(…), and summarize\_text\_column(…) all ran in parallel. This allowed it to complete the task in 3 LLM turns, with the fewest tokens and the fewest steps.

The technical reason behind this behavior is clear: AutoGen’s tool execution engine runs the tool\_calls list returned by the LLM atomically and collects the results in a single conversation step. The framework’s “manage the conversation” philosophy naturally allows multiple parallel channels to be opened at the same time, and the token and latency numbers confirm this directly.

#### LangGraph

LangGraph finished at 9,150 prompt tokens and 70 seconds median, close to AutoGen on tokens but slower on time.Its State Machine architecture displayed both its greatest strength and its most notable weakness simultaneously in Task 5.

In every run, the llm node → tools node → llm node loop accumulates all previous tool outputs in state and passes them to the LLM. This structure guarantees that the agent never forgets anything, which is normally a significant advantage.

However, in Task 5 this strength worked against it. LangGraph was finding the correct tools and building the correct segment. But even after the analysis was complete, it detected ambiguities in the accumulating state, interpreting completed steps as still pending, and repeatedly triggered additional tool calls. Even though it had retrieved the necessary data and was about to produce the correct answer, the state machine’s “missing step” signal kicked in and the agent entered unnecessary loops. As a result, the number of tool calls per run ranged between 6 and 16. The state’s power of “never forgetting anything” sometimes made completed steps appear as incomplete, pulling the agent back into redundant cycles and pushing latency 23 seconds above AutoGen despite a comparable token count.

#### CrewAI

CrewAI’s Task 5 performance produced the highest variance across the entire benchmark. In some runs, it followed a flawless sequence with 5 tool calls, no detours, executing like a script. In these runs, CrewAI’s role and task defined managerial structure worked exactly as intended: when the agent clearly understood its role, it behaved predictably and with discipline.

However, in other runs (e.g., run 16: 35 tool calls), complete chaos ensued. The root cause was the internal monologue (Thought) that CrewAI generates at every step. After correctly building the segment with the right filter, the agent’s inner monologue began questioning whether additional filters should also be applied. After seeing the result, it doubted whether the current segment was valid or the previous one should take precedence. This doubt pushed it to reload the data from scratch. Then it filtered again, entered another verification loop, doubted again, and repeated this spiral 8 times.

In CrewAI, each Thought produces an independent evaluation, and these evaluations occasionally invalidate previously verified steps. The Managerial Process’s “continuous verification” reflex, in some runs, pushed the agent into re-questioning its own correct decisions.

#### LangChain

LangChain’s AgentExecutor structure is inherently sequential, and Task 5 is where that constraint was most visible. At 10,070 prompt tokens and 86 seconds median, it was the slowest framework in this task despite not having the highest token count.

It makes a single tool call at each step, receives the result, then moves on, which means 4 independent tools required 4 separate LLM turns with 4 separate waiting periods. AutoGen’s 47-second median versus LangChain’s 86 seconds is a direct measurement of the cost of sequential versus parallel execution.

In Task 5, LangChain’s tool count settled at either 9 or 15. These two clusters point to two typical strategies: in some runs, it skipped the inspection step and went directly to parsing and summarizing (9 tools), while in others it inspected each column first before processing (15 tools). LangChain’s linear executor identity became clear here: it exhibited neither AutoGen’s parallel efficiency nor CrewAI’s monologue chaos.

### Unstructured data management and framework architecture

The results of this task reveal that how efficiently a framework can manage unstructured data (JSON, LongText) is directly tied to its inner loop mechanism:

Frameworks capable of parallel tool calls (AutoGen) can process independent data columns in a single step. In real-world scenarios involving large JSON objects and numerous text columns, this difference translates into a massive cost and speed advantage.

Frameworks with state-driven loops (LangGraph) excel at data consistency but carry the risk of re-evaluating completed steps accumulated in history.

Monologue-based frameworks (CrewAI) are deeply capable of understanding the type and meaning of data, but this depth sometimes turns into excessive questioning and looping.

Linear execution frameworks (LangChain) process different branches of unstructured data separately, producing a middle-ground result from both worlds.

## GitHub star growth of agentic frameworks

<svg xmlns="http://www.w3.org/2000/svg" width="662.8906860351562" height="500.0000305175781" role="img" focusable="false"><rect width="662.8906860351562" height="500.0000305175781" fill="transparent"></rect><g transform="translate(80,25)"><g transform="translate(0,400.0000305175781)"><g transform="translate(14.060386601386254,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Nov 2022</text></g> <g transform="translate(41.727598946049525,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jan 2023</text></g> <g transform="translate(68.48768957449434,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Mar 2023</text></g> <g transform="translate(96.15490191915761,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">May 2023</text></g> <g transform="translate(123.82211426382088,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jul 2023</text></g> <g transform="translate(151.9428874665934,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Sep 2023</text></g> <g transform="translate(179.61009981125667,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Nov 2023</text></g> <g transform="translate(207.27731215591993,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jan 2024</text></g> <g transform="translate(234.490963642474,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Mar 2024</text></g> <g transform="translate(262.15817598713727,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">May 2024</text></g> <g transform="translate(289.8253883318005,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jul 2024</text></g> <g transform="translate(317.94616153457304,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Sep 2024</text></g> <g transform="translate(345.6133738792363,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Nov 2024</text></g> <g transform="translate(373.2805862238996,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jan 2025</text></g> <g transform="translate(400.04067685234435,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Mar 2025</text></g> <g transform="translate(427.7078891970077,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">May 2025</text></g> <g transform="translate(455.375101541671,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jul 2025</text></g> <g transform="translate(483.4958747444435,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Sep 2025</text></g> <g transform="translate(511.16308708910674,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Nov 2025</text></g> <g transform="translate(538.8302994337699,0)" style="opacity: 1;"><line x1="0" x2="0" y1="0" y2="5" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(0,10) rotate(-60)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">Jan 2026</text></g> <line x1="0" x2="552.8906860351562" y1="0" y2="0" style="stroke: transparent; stroke-width: 1;"></line></g><g transform="translate(0,0)"><g transform="translate(0,400.0000305175781)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">0.0</text></g> <g transform="translate(0,369.23079740084137)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">10k</text></g> <g transform="translate(0,338.46156428410455)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">20k</text></g> <g transform="translate(0,307.69233116736774)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">30k</text></g> <g transform="translate(0,276.923098050631)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">40k</text></g> <g transform="translate(0,246.15386493389425)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">50k</text></g> <g transform="translate(0,215.38463181715744)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">60k</text></g> <g transform="translate(0,184.61539870042068)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">70k</text></g> <g transform="translate(0,153.84616558368387)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">80k</text></g> <g transform="translate(0,123.07693246694713)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">90k</text></g> <g transform="translate(0,92.30769935021031)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">100k</text></g> <g transform="translate(0,61.538466233473564)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">110k</text></g> <g transform="translate(0,30.769233116736757)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">120k</text></g> <g transform="translate(0,0)" style="opacity: 1;"><line x1="0" x2="-5" y1="0" y2="0" style="stroke: rgb(119, 119, 119); stroke-width: 1;"></line><text dominant-baseline="central" text-anchor="end" transform="translate(-10,0) rotate(0)" style="font-family: currentColor; font-size: currentColor; fill: currentColor;">130k</text></g> <line x1="0" x2="0" y1="0" y2="400.0000305175781" style="stroke: transparent; stroke-width: 1;"></line><text transform="translate(-70, 200.00001525878906) rotate(-90)" text-anchor="middle" style="font-family: currentColor; font-size: currentColor; fill: currentColor; dominant-baseline: central;">Github Stars</text></g><path d="M137.883,400L221.338,396.215L234.491,394.185L248.551,392.154L262.158,390.215L276.219,388.185L289.825,386.154L303.886,384.215L317.946,382.185L345.613,380.154L359.22,378.215L373.281,376.185L373.281,374.154L387.341,372.215L400.041,370.185L400.041,370.034L414.101,366.123L427.708,359.938L441.768,356.892L455.375,353.606L469.435,346.462L483.496,344.258L483.496,342.597L497.103,340.745L497.103,338.542L511.163,333.763L538.83,327.637L552.891,325.898" fill="none" stroke-width="3" stroke="#22C55E"></path><path d="M137.883,400L165.55,383.754L165.55,375.538L165.55,367.323L165.55,359.108L179.61,350.892L207.277,342.677L221.338,334.554L248.551,326.338L276.219,318.123L303.886,309.908L331.553,301.692L345.613,293.477L373.281,285.262L387.341,277.046L400.041,274.425L455.375,256.157L469.435,249.892L483.496,248.191L483.496,246.803L497.103,245.234L497.103,243.372L511.163,239.923L538.83,234.828L552.891,233.443" fill="none" stroke-width="3" stroke="#8B5CF6"></path><path d="M179.61,400L207.277,388.738L207.277,383.015L221.338,377.292L234.491,371.569L248.551,365.846L262.158,360.123L262.158,354.308L289.825,348.585L317.946,342.862L331.553,337.138L359.22,331.415L373.281,325.692L387.341,319.969L400.041,314.148L427.708,303.538L455.375,296.615L469.435,289.818L483.496,285.8L483.496,282.778L497.103,281.04L497.103,278.978L511.163,274.268L538.83,267.969L552.891,266.258" fill="none" stroke-width="3" stroke="#FF8C00"></path><path d="M262.158,400L331.553,388.462L331.553,380.615L331.553,372.862L331.553,368.892L331.553,365.015L331.553,361.138L331.553,357.169L345.613,353.292L359.22,349.415L373.281,345.446L400.041,341.569L400.041,341.434L441.768,338.523L455.375,338.412L469.435,337.631L483.496,337.44L483.496,337.265L497.103,337.071L497.103,336.84L511.163,336.48L538.83,335.978L552.891,335.791" fill="none" stroke-width="3" stroke="#FFD700"></path><path d="M0,400L27.667,396.308L41.728,387.385L55.788,380L68.488,353.846L82.548,323.077L110.215,276.923L137.883,233.846L165.55,196.923L193.217,166.154L221.338,141.538L262.158,116.923L303.886,104.615L345.613,98.462L373.281,95.385L400.041,94L455.375,59.803L469.435,50.178L483.496,47.117L483.496,44.769L497.103,41.815L497.103,38.305L511.163,28.662L538.83,16.582L552.891,13.425" fill="none" stroke-width="3" stroke="#1F1F1F"></path><g><g transform="translate(137.88250086520713, 400.0000305175781)" focusable="false" data-testid="line.point.LangGraph.0" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(221.33769875730619, 396.21541484421954)" focusable="false" data-testid="line.point.LangGraph.1" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(234.490963642474, 394.18464545851486)" focusable="false" data-testid="line.point.LangGraph.2" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(248.55135024386024, 392.15387607281025)" focusable="false" data-testid="line.point.LangGraph.3" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(262.15817598713727, 390.21541438645585)" focusable="false" data-testid="line.point.LangGraph.4" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(276.2185625885235, 388.18464500075123)" focusable="false" data-testid="line.point.LangGraph.5" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(289.8253883318005, 386.15387561504656)" focusable="false" data-testid="line.point.LangGraph.6" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(303.8857749331868, 384.21541392869216)" focusable="false" data-testid="line.point.LangGraph.7" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(317.94616153457304, 382.18464454298754)" focusable="false" data-testid="line.point.LangGraph.8" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(345.6133738792363, 380.1538751572829)" focusable="false" data-testid="line.point.LangGraph.9" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(359.22019962251335, 378.21541347092847)" focusable="false" data-testid="line.point.LangGraph.10" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 376.18464408522385)" focusable="false" data-testid="line.point.LangGraph.11" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 374.15387469951924)" focusable="false" data-testid="line.point.LangGraph.12" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(387.34097282528586, 372.21541301316483)" focusable="false" data-testid="line.point.LangGraph.13" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 370.18464362746016)" focusable="false" data-testid="line.point.LangGraph.14" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 370.0338743851882)" focusable="false" data-testid="line.point.LangGraph.15" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(414.1010634537306, 366.12310485605093)" focusable="false" data-testid="line.point.LangGraph.16" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(427.7078891970077, 359.93848899958687)" focusable="false" data-testid="line.point.LangGraph.17" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(441.768275798394, 356.89233492102994)" focusable="false" data-testid="line.point.LangGraph.18" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(455.375101541671, 353.60618082416244)" focusable="false" data-testid="line.point.LangGraph.19" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(469.4354881430572, 346.46156489445616)" focusable="false" data-testid="line.point.LangGraph.20" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 344.2584878032978)" focusable="false" data-testid="line.point.LangGraph.21" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 342.59694921499397)" focusable="false" data-testid="line.point.LangGraph.22" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 340.7446413813664)" focusable="false" data-testid="line.point.LangGraph.23" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 338.54156429020804)" focusable="false" data-testid="line.point.LangGraph.24" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(511.16308708910674, 333.76310238717883)" focusable="false" data-testid="line.point.LangGraph.25" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(538.8302994337699, 327.6369480736366)" focusable="false" data-testid="line.point.LangGraph.26" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(552.8906860351562, 325.8984864025409)" focusable="false" data-testid="line.point.LangGraph.27" style="pointer-events: none;"><circle r="6" fill="#22C55E" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(137.88250086520713, 400.0000305175781)" focusable="false" data-testid="line.point.AutoGen.0" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(165.54971320987042, 383.7538754319411)" focusable="false" data-testid="line.point.AutoGen.1" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(165.54971320987042, 375.5384901897724)" focusable="false" data-testid="line.point.AutoGen.2" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(165.54971320987042, 367.32310494760367)" focusable="false" data-testid="line.point.AutoGen.3" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(165.54971320987042, 359.10771970543493)" focusable="false" data-testid="line.point.AutoGen.4" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(179.61009981125667, 350.89233446326625)" focusable="false" data-testid="line.point.AutoGen.5" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(207.27731215591993, 342.67694922109746)" focusable="false" data-testid="line.point.AutoGen.6" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(221.33769875730619, 334.553871678279)" focusable="false" data-testid="line.point.AutoGen.7" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(248.55135024386024, 326.3384864361103)" focusable="false" data-testid="line.point.AutoGen.8" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(276.2185625885235, 318.1231011939415)" focusable="false" data-testid="line.point.AutoGen.9" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(303.8857749331868, 309.90771595177284)" focusable="false" data-testid="line.point.AutoGen.10" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 301.6923307096041)" focusable="false" data-testid="line.point.AutoGen.11" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(345.6133738792363, 293.47694546743537)" focusable="false" data-testid="line.point.AutoGen.12" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 285.2615602252667)" focusable="false" data-testid="line.point.AutoGen.13" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(387.34097282528586, 277.04617498309796)" focusable="false" data-testid="line.point.AutoGen.14" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 274.424636321552)" focusable="false" data-testid="line.point.AutoGen.15" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(455.375101541671, 256.15694262014534)" focusable="false" data-testid="line.point.AutoGen.16" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(469.4354881430572, 249.8923267575778)" focusable="false" data-testid="line.point.AutoGen.17" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 248.19078816622223)" focusable="false" data-testid="line.point.AutoGen.18" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 246.8030957526574)" focusable="false" data-testid="line.point.AutoGen.19" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 245.23386486370381)" focusable="false" data-testid="line.point.AutoGen.20" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 243.37232626014122)" focusable="false" data-testid="line.point.AutoGen.21" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(511.16308708910674, 239.92309522775503)" focusable="false" data-testid="line.point.AutoGen.22" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(538.8302994337699, 234.82771022362343)" focusable="false" data-testid="line.point.AutoGen.23" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(552.8906860351562, 233.44309473337026)" focusable="false" data-testid="line.point.AutoGen.24" style="pointer-events: none;"><circle r="6" fill="#8B5CF6" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(179.61009981125667, 400.0000305175781)" focusable="false" data-testid="line.point.CrewAI.0" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(207.27731215591993, 388.73849119685246)" focusable="false" data-testid="line.point.CrewAI.1" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(207.27731215591993, 383.0154138371394)" focusable="false" data-testid="line.point.CrewAI.2" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(221.33769875730619, 377.2923364774264)" focusable="false" data-testid="line.point.CrewAI.3" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(234.490963642474, 371.56925911771333)" focusable="false" data-testid="line.point.CrewAI.4" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(248.55135024386024, 365.8461817580003)" focusable="false" data-testid="line.point.CrewAI.5" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(262.15817598713727, 360.12310439828724)" focusable="false" data-testid="line.point.CrewAI.6" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(262.15817598713727, 354.307719339224)" focusable="false" data-testid="line.point.CrewAI.7" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(289.8253883318005, 348.584641979511)" focusable="false" data-testid="line.point.CrewAI.8" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(317.94616153457304, 342.86156461979795)" focusable="false" data-testid="line.point.CrewAI.9" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 337.13848726008484)" focusable="false" data-testid="line.point.CrewAI.10" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(359.22019962251335, 331.41540990037186)" focusable="false" data-testid="line.point.CrewAI.11" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 325.6923325406588)" focusable="false" data-testid="line.point.CrewAI.12" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(387.34097282528586, 319.96925518094577)" focusable="false" data-testid="line.point.CrewAI.13" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 314.1477162752592)" focusable="false" data-testid="line.point.CrewAI.14" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(427.7078891970077, 303.5384846966083)" focusable="false" data-testid="line.point.CrewAI.15" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(455.375101541671, 296.6154072453425)" focusable="false" data-testid="line.point.CrewAI.16" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(469.4354881430572, 289.8184836498554)" focusable="false" data-testid="line.point.CrewAI.17" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 285.8000218048096)" focusable="false" data-testid="line.point.CrewAI.18" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 282.778483112746)" focusable="false" data-testid="line.point.CrewAI.19" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 281.04002144165037)" focusable="false" data-testid="line.point.CrewAI.20" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 278.978482822829)" focusable="false" data-testid="line.point.CrewAI.21" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(511.16308708910674, 274.2677132326566)" focusable="false" data-testid="line.point.CrewAI.22" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(538.8302994337699, 267.9692512136606)" focusable="false" data-testid="line.point.CrewAI.23" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(552.8906860351562, 266.25848185237004)" focusable="false" data-testid="line.point.CrewAI.24" style="pointer-events: none;"><circle r="6" fill="#FF8C00" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(262.15817598713727, 400.0000305175781)" focusable="false" data-testid="line.point.OpenAI Swarm.0" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 388.4615680988018)" focusable="false" data-testid="line.point.OpenAI Swarm.1" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 380.61541365403394)" focusable="false" data-testid="line.point.OpenAI Swarm.2" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 372.8615669086163)" focusable="false" data-testid="line.point.OpenAI Swarm.3" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 368.8923358365572)" focusable="false" data-testid="line.point.OpenAI Swarm.4" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 365.0154124638484)" focusable="false" data-testid="line.point.OpenAI Swarm.5" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 361.1384890911396)" focusable="false" data-testid="line.point.OpenAI Swarm.6" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(331.5529872778501, 357.16925801908053)" focusable="false" data-testid="line.point.OpenAI Swarm.7" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(345.6133738792363, 353.2923346463717)" focusable="false" data-testid="line.point.OpenAI Swarm.8" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(359.22019962251335, 349.41541127366287)" focusable="false" data-testid="line.point.OpenAI Swarm.9" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 345.44618020160385)" focusable="false" data-testid="line.point.OpenAI Swarm.10" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 341.569256828895)" focusable="false" data-testid="line.point.OpenAI Swarm.11" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 341.43387220318135)" focusable="false" data-testid="line.point.OpenAI Swarm.12" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(441.768275798394, 338.52310275033807)" focusable="false" data-testid="line.point.OpenAI Swarm.13" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(455.375101541671, 338.4123335111178)" focusable="false" data-testid="line.point.OpenAI Swarm.14" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(469.4354881430572, 337.6307949899527)" focusable="false" data-testid="line.point.OpenAI Swarm.15" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 337.44002574462894)" focusable="false" data-testid="line.point.OpenAI Swarm.16" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 337.2646411158635)" focusable="false" data-testid="line.point.OpenAI Swarm.17" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 337.0707949472281)" focusable="false" data-testid="line.point.OpenAI Swarm.18" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 336.8400256988525)" focusable="false" data-testid="line.point.OpenAI Swarm.19" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(511.16308708910674, 336.48002567138667)" focusable="false" data-testid="line.point.OpenAI Swarm.20" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(538.8302994337699, 335.97848717158394)" focusable="false" data-testid="line.point.OpenAI Swarm.21" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(552.8906860351562, 335.7907948495718)" focusable="false" data-testid="line.point.OpenAI Swarm.22" style="pointer-events: none;"><circle r="6" fill="#FFD700" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(0, 400.0000305175781)" focusable="false" data-testid="line.point.LangChain.0" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(27.667212344663273, 396.3077225435697)" focusable="false" data-testid="line.point.LangChain.1" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(41.727598946049525, 387.38464493971605)" focusable="false" data-testid="line.point.LangChain.2" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(55.78798554743578, 380.0000289916992)" focusable="false" data-testid="line.point.LangChain.3" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(68.48768957449434, 353.84618084247296)" focusable="false" data-testid="line.point.LangChain.4" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(82.54807617588058, 323.0769477257362)" focusable="false" data-testid="line.point.LangChain.5" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(110.21528852054387, 276.923098050631)" focusable="false" data-testid="line.point.LangChain.6" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(137.88250086520713, 233.8461716871995)" focusable="false" data-testid="line.point.LangChain.7" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(165.54971320987042, 196.9230919471154)" focusable="false" data-testid="line.point.LangChain.8" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(193.21692555453367, 166.1538588303786)" focusable="false" data-testid="line.point.LangChain.9" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(221.33769875730619, 141.53847233698917)" focusable="false" data-testid="line.point.LangChain.10" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(262.15817598713727, 116.92308584359975)" focusable="false" data-testid="line.point.LangChain.11" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(303.8857749331868, 104.61539259690502)" focusable="false" data-testid="line.point.LangChain.12" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(345.6133738792363, 98.4615459735577)" focusable="false" data-testid="line.point.LangChain.13" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(373.2805862238996, 95.38462266188404)" focusable="false" data-testid="line.point.LangChain.14" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(400.04067685234435, 94.00000717163086)" focusable="false" data-testid="line.point.LangChain.15" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(455.375101541671, 59.80308148568962)" focusable="false" data-testid="line.point.LangChain.16" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(469.4354881430572, 50.17846536677435)" focusable="false" data-testid="line.point.LangChain.17" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 47.11692667165901)" focusable="false" data-testid="line.point.LangChain.18" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(483.4958747444435, 44.769234184852)" focusable="false" data-testid="line.point.LangChain.19" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 41.8153878056453)" focusable="false" data-testid="line.point.LangChain.20" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(497.1027004877205, 38.30461830702561)" focusable="false" data-testid="line.point.LangChain.21" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(511.16308708910674, 28.66154064824032)" focusable="false" data-testid="line.point.LangChain.22" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(538.8302994337699, 16.58153972660946)" focusable="false" data-testid="line.point.LangChain.23" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g><g transform="translate(552.8906860351562, 13.42461640883224)" focusable="false" data-testid="line.point.LangChain.24" style="pointer-events: none;"><circle r="6" fill="#1F1F1F" stroke="transparent" stroke-width="0" style="pointer-events: none;"></circle></g></g><g transform="translate(0,0)"><rect data-ref="mesh-interceptor" width="552.8906860351562" height="400.0000305175781" fill="red" opacity="0" style="cursor: auto;"></rect></g></g></svg>

## Compare agentic AI frameworks

| Framework | Pros✅ | Cons❌ |
| --- | --- | --- |
| LangGraph | • Graph-based orchestration with state management   • Supports in-thread and cross-thread memory   • Custom breakpoints for human input   • Highly modular, useful for enterprise logic | • Steep learning curve   • Documentation still maturing   • More rigid than adaptive frameworks |
| AutoGen | • Adaptive and asynchronous agent interactions   • Low-code support   • Human-in-the-loop via UserProxyAgent | • No built-in persistent memory   • Difficult to manage in large-scale deployments |
| CrewAI | • Easy role-based YAML configuration   • Built-in memory   • Human-in-the-loop configurable | • Python-centric design   • Focused on linear task flows |
| OpenAI Swarm | • Natural language routine definitions   • Lightweight and fast to prototype   • Flexible, prompt-based logic | • No built-in memory   • No formal orchestration or state model   • No native human-in-the-loop support |
| LangChain | • Wide integration support (APIs, databases, vector stores)   • Modular components: chains, tools, memory, basic agents   • Strong for RAG and tool-augmented workflows   • Mature documentation and large community | • Basic agent framework, lacks advanced orchestration   • No graph-based or role-based models   • Multi-agent setups require manual composition   • Performance overhead in deep chains |

Agentic AI frameworks vary across several key dimensions, and understanding these differences is essential for making meaningful comparisons.

## Multi-agent orchestration

[Multi-agent orchestration](https://aimultiple.com/agentic-orchestration) coordinates multiple specialized AI agents to tackle complex workflows that exceed single-agent capabilities. Rather than building one monolithic agent, orchestration divides work among agents with distinct roles, tools, and expertise. Each framework offers different approaches to agent coordination.

| Framework | Multi-agent orchestration | Ease of use |
| --- | --- | --- |
| LangGraph (Graph-Based) | Centralized: Graph-based multi-agent flows | **Complex:** Requires understanding acyclic graph structures |
| AutoGen (Adaptive) | Adaptive orchestration | **Moderate:** Conversational agent interactions simplify usage |
| CrewAI (Role-Based) | Hierarchical: Role-based multi-agent flows | **Easy:** Structured, role-based design makes it easy to start |
| OpenAI Swarm (Routine-Based) | No defined control flow (routine-based prompting patterns) | **Easy:** Lightweight and routine-based |
| LangChain (Chain-Based) | Linear or nested chains with optional agent support | **Moderate:** Good for pipelines, but multi-agent orchestration needs manual setup |

### LangGraph

![](https://aimultiple.com/wp-content/uploads/2025/06/LangGraph-architecture-1200x629.png.webp)

*LangGraph framework*

LangGraph is a relatively well-known framework and stands out as a key option for developers building agent systems.

**Explicit multi-agent coordination:** You can model **multiple agents** as individual nodes or groups, each with its own logic, memory, and role in the system.

It creates AI workflows across APIs and tools. Thus, it is a good fit for [RAG](https://aimultiple.com/agentic-rag) and custom pipelines.

### AutoGen

![](https://aimultiple.com/wp-content/uploads/2025/06/AutoGen-architecture-1200x594.png.webp)

*AutoGen Framework [<sup>1</sup>](#easy-footnote-bottom-1-147948 "https://dev.to/thenomadevel/top-5-frameworks-for-building-ai-agents-in-2024-g2m")*

AutoGen allows multiple agents to communicate by passing messages in a loop. Each agent can respond, reflect, or call tools based on its internal logic.

It has an asynchronous agent collaboration, making it particularly useful for research and prototyping scenarios where agent behavior requires experimentation or iterative refinement.

### CrewAI

![](https://aimultiple.com/wp-content/uploads/2025/06/CrewAI-multi-agentic-systems-1200x813.png.webp)

*Crew AI [<sup>2</sup>](#easy-footnote-bottom-2-147948 "https://dev.to/thenomadevel/top-5-frameworks-for-building-ai-agents-in-2024-g2m")*

CrewAI handles most of the low-level logic for you and provides multi-agent orchestration:

- Integrates with monitoring tools for tracing and debugging
- Built-in execution control through Flows with conditional logic, loops, and state management
- Supports hierarchical (manager-worker) and structured multi-agent coordination

### OpenAI Swarm

![](https://aimultiple.com/wp-content/uploads/2025/06/OpenAI-Swarm-framework-1200x641.png.webp)

Swarm framework

**Swarm** is a lightweight, experimental multi-agent framework for prototyping. Agents work sequentially through handoffs, transferring tasks while maintaining shared context. It uses natural language routines and Python tools for flexible workflows.

### LangChain

LangChain is a framework for building single-agent LLM applications with RAG tooling. It provides modular components including chains, tools, memory, and retrieval for document processing workflows.

LangChain operates primarily through single-agent execution patterns where one agent manages the workflow.

## Agent and function definition

| Framework | Agent definition | Function definition |
| --- | --- | --- |
| LangGraph (Graph-Based) | Nodes that maintain a state | Annotations (structured & explicit functions) |
| AutoGen (Adaptive) | Agents with flexible routing | Annotations (structured & explicit functions) |
| CrewAI (Role-Based) | Agents with skills and associated tasks | Annotations (structured & explicit functions) |
| OpenAI Swarm (Routine-Based) | Agents with routines and functions | Docstrings (general-purpose functions) |
| LangChain (Chain-Based) | Agent(s) coordinating calls to LLMs and tools (central orchestrator) | Function calls with explicit interfaces (toolkits, prompt templates) |

### LangGraph

LangGraph takes a **graph-based approach** to agent design, where each agent is represented as a node that maintains its own state. These nodes are connected through a directed graph, enabling conditional logic, multi-team coordination, and hierarchical control. This enables you build and visualize multi-agent graphs with supervisor nodes for scalable orchestration.

LangGraph uses **annotated, structured functions** that attach tools to agents. You can build out nodes, connect them to various supervisors, and visualize how different teams interact. Think of it like giving each team member a detailed job description. This makes it easier to build and test agents that work together.

### AutoGen

AutoGen defines agents as **adaptive units** capable of flexible routing and asynchronous communication. Agents interact with each other (and optionally with humans) by exchanging messages, allowing for collaborative problem-solving. Like LangGraph uses **annotated, structured functions**.

### CrewAI

CrewAI takes a **role-based design** approach. Each agent is assigned a role (e.g., Researcher, Developer) and a set of skills, functions or tools it can access. Function definition is through **structured annotations**.

### OpenAI Swarm

OpenAI Swarm uses a **routine-based model** where agents are defined through prompts and function docstrings. It doesn’t have formal orchestration or state models, relying instead on manually structured workflows. Functions behavior is inferred by the LLM through **docstrings** (Swarm identifies what a function does by reading its description) making this setup flexible but less precise.

### LangChain

LangChain uses a chain-based architecture where a single orchestrator agent manages calls to language models and various tools. It defines functions through explicit interfaces like toolkits and prompt templates.

While primarily focused on centralized workflows, LangChain supports extensions for multi-agent setups but lacks built-in agent-to-agent communication.

## Memory

| Framework | Stateful | Contextual | Memory features |
| --- | --- | --- | --- |
| LangGraph (Graph-Based) | ✅ | ✅ | • Short-term: Customizable   • Long-term: External integrations   • Entity memory: Fully supported |
| AutoGen (Adaptive) | ❌ | ✅ | • Short-term: Message lists   • Long-term: External integrations   • Entity memory: Not supported |
| CrewAI (Role-Based) | ✅ | ✅ | • Short-term: RAG, Contextual   • Long-term: SQLite3 DB   • Entity memory: Supported via RAG |
| OpenAI Swarm (Routine-Based) | ❌ | Manual contextual memory | • Short-term: Context variables   • Long-term: External integrations   • Entity memory: Not supported |
| LangChain (Chain-Based) | ✅ | ✅ | • Short-term: In-memory or cache-based (e.g., conversation history)   • Long-term: Supports external memory integrations (databases, vector stores, etc.)   • Entity memory: Supported via retrieval and embeddings-based methods |

**Memory capabilities**:

- **Stateful**: Whether the framework supports persistent memory across executions.
- **Contextual**: Whether it supports short-term memory via message history or context passing.

**Memory features** is a key part of building agentic systems to remember context and adapt over time:

- **Short-term memory**: Keeps track of recent interactions, enabling agents to handle multi-turn conversations or step-by-step workflows.
- **Long-term memory**: Stores persistent information across sessions, such as user preferences or task history.
- **Entity memory**: Tracks and updates knowledge about specific objects, people, or concepts mentioned during interactions (e.g., remembering a company name or project ID mentioned earlier).

### LangGraph

LangGraph uses two types of memory: **in-thread memory**, which stores information during a single task or conversation, and **cross-thread memory**, which saves data across sessions. Developers can use `MemorySaver` to save the flow of a task and link it to a specific `thread_id`. For long-term storage, LangGraph supports tools like `InMemoryStore` or other databases. This provides flexible control over how memory is scoped and retained across executions.

### AutoGen

AutoGen uses a **contextual memory model**. Each agent maintains short-term context through a `context_variables` object, which stores interaction history. It doesn’t have built-in persistent memory.

### CrewAI

CrewAIprovides layered memory out of the box. It stores short-term memory in a ChromaDB vector store, recent task results in SQLite, and long-term memory in a separate SQLite table (based on task descriptions). Additionally, it supports entity memory using vector embeddings. This memory setup is automatically configured when memory=True is enabled,

### OpenAI Swarm

Swarm is **stateless** and does not manage memory natively. Developers can pass short-term memory through `context_variables` manually, and optionally integrate external tools or third-party memory layers (e.g., mem0) to store longer-term context.

### LangChain

LangChain supports both short-term and long-term memory through flexible components. Short-term memory is typically managed via in-memory buffers that track conversation history within a session. For long-term memory, LangChain integrates with external vector stores or databases to persist embeddings and retrieval data.

Developers can customize memory scopes and strategies using built-in memory classes, enabling efficient management of contextual and entity-specific memory across interactions.

## Human-in-the-loop

| Framework | Human-in-the-loop |
| --- | --- |
| LangGraph (Graph-Based) | Custom breakpoints for human input |
| AutoGen (Adaptive) | Requests feedback after agent execution |
| CrewAI (Role-Based) | Requests feedback after agent execution |
| OpenAI Swarm (Routine-Based) | N/A (human-as-a-tool) |
| LangChain (Chain-Based) | Supports custom breakpoints and user interactions within workflows for human feedback and intervention |

### LangGraph

LangGraph supports custom breakpoints (`interrupt_before`) to pause the graph and wait for user input mid-execution.

### AutoGen

AutoGen natively supports human agents via `UserProxyAgent`, allowing humans to review, approve, or modify steps during agent collaboration.

### CrewAI:

CrewA **I** enables feedback after each task by setting `human_input=True`; the agent pauses to collect natural language input from the user.

### OpenAI Swarm

OpenAI Swarm offers no built-in HITL.

### LangChain

LangChain allows inserting custom breakpoints within chains or agents to pause execution and request human input. This supports review, feedback, or manual intervention at defined points in the workflow.

## Model Context Protocol (MCP) integration in agentic AI frameworks

AI agents need to interact with external tools like databases, APIs, file systems, and business applications. Without a standard, each framework had to build custom integrations for every tool, creating a fragmented ecosystem. MCP solves this by providing a universal protocol that lets any agent connect to any tool through a single interface.

### How each framework integrates with MCP

**LangGraph**  
LangGraph connects to MCP servers through an adapter that automatically discovers available tools and converts them into LangChain-compatible format. Agents can then use these tools seamlessly alongside their native capabilities.

**AutoGen**  
AutoGen provides built-in MCP integration through its extension module. Developers can connect to MCP servers and make all their tools available to AutoGen agents with just a few lines of code.

**CrewAI**  
CrewAI agents can directly reference MCP servers in their configuration using simple URLs or structured settings. The framework handles connection lifecycle and error management automatically.

**OpenAI Swarm**  
Swarm benefits from OpenAI’s native MCP support across its ecosystem. Since OpenAI integrated MCP into ChatGPT and its Agents SDK, Swarm can leverage this infrastructure directly.

**LangChain**  
LangChain offers MCP tool-calling capabilities where Python functions act as bridges to MCP servers. This enables pulling tools from various sources and integrating them into chains, agents, and other LangChain components without custom wrappers.

## What agentic AI frameworks actually do?

Agentic AI frameworks assist with prompt engineering and managing how **data flows to and from LLMs**. At a basic level, they help **structure prompts** so the LLM responds in a predictable format and route responses to the right tool, API, or document.

If building from scratch, you would manually define the prompt, extract the tool the LLM wants to use, and trigger the corresponding API call. Frameworks streamline this by:

- **Prompt orchestration**: Building, managing, and routing complex prompts to LLMs
- **Tool integration**: Letting agents call external APIs, databases, code functions, etc.
- **Memory**: Maintaining state across turns or sessions (short- and long-term)
- **RAG integration**: Enabling knowledge retrieval from external sources
- **Multi-agent coordination**: Structuring how agents collaborate or delegate tasks
![](https://aimultiple.com/wp-content/uploads/2025/06/agentic-AI-framework-architecture-1200x816.png.webp)

*Agentic framework [<sup>3</sup>](#easy-footnote-bottom-3-147948 "https://sashapasmanik.substack.com/p/agentic-ai-and-automation")*

## Agentic AI frameworks: Real life use cases

### LangGraph – Multi-agent travel planner

A production project built with LangGraph demonstrates a **stateful, multi-agent travel assistant** that pulls flight and hotel data (using Google Flights & Hotels APIs) and generates travel recommendations.[<sup>4</sup>](#easy-footnote-bottom-4-147948 "https://medium.com/@jalajagr/automate-your-travel-plans-with-multi-agent-ai-langgraph-14d688baed66")

### CrewAI – Agentic content creator

CrewAI’s official examples repository includes flows like **trip planning**, **marketing strategy**, **stock analysis**, and **recruitment assistants**, where role-specific agents (e.g., “Researcher”, “Writer”) collaborate on tasks.[<sup>5</sup>](#easy-footnote-bottom-5-147948 "https://docs.crewai.com/getting-started/examples")

CrewAI turns a high-level content brief into a complete article using Groq.

## Core features of agentic AI frameworks

**Model support**:

- Most are **model-agnostic**, supporting multiple LLM providers (e.g., OpenAI, Anthropic, open-source models).
- However, **system prompt structures vary** by framework and may perform better with some models than others.
- **Access to and customization of system prompts** is often essential for optimal results.

**Tooling**:

- All frameworks support **tool use**, a core part of enabling agent actions.
- Offer **simple abstractions** to define custom tools.
- Most support **Model-Context-Protocol (MCP)**, either natively or through community extensions.

**Memory / State**:

- Use **state tracking** to maintain short-term memory across steps or LLM calls.
- Some helps agents **retain prior interactions or context** within a session.

**RAG (Retrieval-Augmented Generation)**:

- Most include **easy setup options for RAG**, integrating vector databases or document stores.
- This allows agents to **reference external knowledge** during execution.

### Other common features

- Support for **asynchronous execution**, enabling concurrent agent or tool calls.
- Built-in handling for **structured outputs** (e.g., JSON).
- Support for **streaming outputs** where the model generates results incrementally.
- Basic **observability features** for monitoring and debugging agent runs.

## Benchmark methodology

**1\. Task Structure**

Task 1: Measures whether a single tool call can be made with the correct parameter. The framework’s base infrastructure overhead is most clearly revealed in this simple scenario.

Task 2: Requires holding the results of two separate filter groups in memory and combining them into a single output. State management and multi-segment coordination are tested.

Task 3: Measures whether numerical conditions in natural language are translated into tool parameters without distortion. The real test is whether the framework’s retry and re-prompt mechanisms can preserve these parameters.

Task 4: A tool throws Network, Timeout, and RateLimit errors in succession. Whether the framework changes strategy in the face of these errors is measured.

Task 5: The agent must first discover JSON and LongText columns, then call the correct tools with the correct scope parameters. Whether the framework executes independent tools in parallel or sequentially is observed.

**2\. Configuration**

All frameworks used the same LLM model (openai/gpt-5.2) and the same temperature value (0.1). For all tasks, each agent was given the same tools and the same prompts. Each framework was set up in its native structure: LangChain with AgentExecutor, LangGraph with StateGraph, AutoGen with AssistantAgent + UserProxyAgent, and CrewAI with Agent + Task + Crew.

The IBM Telco Customer Churn dataset (7,032 customers) was used. Tool state was reset before each run. 100 independent runs were executed for each framework and task combination.

Max iteration limits were set according to task complexity: 10 for Tasks 1, 2, and 3; 20 for Task 4 due to the flaky tool loop; and 20 for Task 5 due to the 4-step discovery chain.

## Reference Links

[

1.

Top 5 Frameworks for Building AI Agents in 2024 (Plus 1 Bonus) - DEV Community

DEV Community

](https://dev.to/thenomadevel/top-5-frameworks-for-building-ai-agents-in-2024-g2m)[

2.

Top 5 Frameworks for Building AI Agents in 2024 (Plus 1 Bonus) - DEV Community

DEV Community

](https://dev.to/thenomadevel/top-5-frameworks-for-building-ai-agents-in-2024-g2m)[

3.

Agentic AI and Automation - by Sasha Pasmanik

Stay Curious

](https://sashapasmanik.substack.com/p/agentic-ai-and-automation)[

4.

Automate Your Travel Plans with Multi-Agent AI &amp; LangGraph | by Jalaj Agrawal | Medium

Medium

](https://medium.com/@jalajagr/automate-your-travel-plans-with-multi-agent-ai-langgraph-14d688baed66)[

5.

CrewAI Documentation - CrewAI

Mintlify

](https://docs.crewai.com/getting-started/examples)

Cem has been the principal analyst at AIMultiple since 2017. AIMultiple informs hundreds of thousands of businesses (as per similarWeb) including 55% of Fortune 500 every month.  
  
Cem's work has been cited by leading global publications including Business Insider, Forbes, Washington Post, global firms like Deloitte, HPE and NGOs like World Economic Forum and supranational organizations like European Commission. You can see more reputable companies and resources that referenced AIMultiple.  
  
Throughout his career, Cem served as a tech consultant, tech buyer and tech entrepreneur. He advised enterprises on their technology decisions at McKinsey & Company and Altman Solon for more than a decade. He also published a McKinsey report on digitalization.  
  
He led technology strategy and procurement of a telco while reporting to the CEO. He has also led commercial growth of deep tech company Hypatos that reached a 7 digit annual recurring revenue and a 9 digit valuation from 0 within 2 years. Cem's work in Hypatos was covered by leading technology publications like TechCrunch and Business Insider.  
  
Cem regularly speaks at international technology conferences. He graduated from Bogazici University as a computer engineer and holds an MBA from Columbia Business School.

Researched by

Nazlı Şipi

AI Researcher

Nazlı is a data analyst at AIMultiple. She has prior experience in data analysis across various industries, where she worked on transforming complex datasets into actionable insights.

We follow [ethical norms](https://aimultiple.com/commitments) & [our process](https://aimultiple.com/methodology) for objectivity. AIMultiple's [customers](https://aimultiple.com/funding) in [Agentic AI Frameworks](https://aimultiple.com/agentic-ai-frameworks) include Creatio, Tidio, Weights & Biases.

How likely are you to recommend us to a friend or colleague?

Not likely

Extremely likely