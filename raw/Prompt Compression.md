---
title: "Prompt Compression"
source: "https://www.ibm.com/think/tutorials/prompt-compression"
author:
  - "[[Nivetha Suruliraj]]"
published:
created: 2026-05-08
description: "Prompt compression is the process of reducing the size of input context while preserving the most relevant semantic information required for a task."
tags:
  - "clippings"
---
## Introduction

Large language models (LLMs) are widely used across applications such as chatbots, question-answering systems and enterprise workflows. Yet behind their seamless responses lies a growing challenge: these systems must continuously process and reason over vast, unstructured streams of information, including multi-turn conversations, logs and contextual data. As the volume of input increases, managing prompt size and relevance becomes critical for maintaining efficiency and performance.

One key challenge in such systems is managing increasingly large input contexts. As prompt size grows, it drives up computational cost, impacts response latency and strains the model’s limited context window, often resulting in truncated inputs or inefficient use of tokens. 

Prompt compression addresses this challenge by reducing input size while preserving essential information. It is a foundational design pattern for building efficient, scalable and cost-effective AI systems.

## What is prompt compression?

Prompt compression is an optimization technique in natural language processing and machine learning that reduces the size of the input prompt while preserving essential information. By removing redundant details and retaining only high-value information, prompt compression enables more efficient and focused LLM processing.

Instead of sending the full original prompt directly:

Original prompt → LLM inference

We introduce a prompt compressor:

Original prompt → Compressor → Optimized input prompt → LLM

The prompt compressor acts as an intermediate processing layer that filters irrelevant content, summarizes key information and optimizes token usage before passing the input to the model.

The goal is to,

- Reduce prompt length
- Minimize the number of tokens
- Retain only meaningful information

Prompt compression is especially important in,

- Retrieval-augmented generation (RAG) systems
- Chatbots with long conversation history
- Enterprise workflows with long context

In enterprise workflows, long context often includes large volumes of structured and unstructured data such as logs, reports, transaction records and multi-step process histories. These inputs can quickly exceed token limits or introduce noise, making it difficult for models to focus on relevant information. Prompt compression helps the data into concise, high-value inputs that improve both efficiency and accuracy.

## Why prompt compression matters?

1\. Token limits and context window

LLMs operate within a fixed context window, which is the maximum amount of text (tokens) the model can process at once. In real-world scenarios such as RAG systems or chatbots with long conversation histories, inputs can quickly exceed these limits. Prompt compression ensures that essential information fits within the available context, avoiding truncation and loss of important details.

2\. Cost optimization

LLM usage is often priced based on the number of tokens processed. In applications that handle large volumes of data such as enterprise workflows or customer support systems, long prompts can significantly increase operational costs. By reducing token count, prompt compression helps make these systems more cost-efficient.

3\. Faster inference

Larger prompts require more processing time, which can slow down response generation. This is especially noticeable in real-time applications like chatbots or interactive assistants. Compressing prompts reduces input size, resulting in faster inference and improved user experience.

4\. Better accuracy

Long inputs often contain redundant or irrelevant information that can distract the model. By removing noise and retaining only essential information, prompt compression helps the model focus on what matters, leading to more accurate and reliable responses.

## Prompt compression techniques

Prompt compression is not a single method, but a combination of techniques used to reduce prompt length, optimize token counts and preserve key information for effective LLM inference.

In practice, these techniques are applied together as part of a context compression pipeline, especially in systems handling long prompts and large context such as chatbots, RAG pipelines and enterprise NLP workflows.

Running example:

We will use the same example across techniques,

Original:   
Customer John reported unstable internet for 3 days with video call disruptions.

**1. Extractive compression**

Extractive compression selects the most relevant parts of the input while removing redundant or low-value content. This is supported by NLP techniques such as Named Entity Recognition (NER) and keyword extraction. NER helps identify important entities like “John,” while keyword extraction highlights critical terms such as “internet” and “video issues.” Together, these techniques help the model focus on high-value information.

**Extracted:**   
John: unstable internet, 3 days, video issues

When to use?

- Long, descriptive inputs
- Logs, tickets or incident reports
- When key details must be preserved

**2\. Summarization**

Summarization converts extracted content into a concise and readable representation. Modern LLMs use abstractive summarization, where they understand the meaning of the input and rewrite it in a shorter form rather than copying text directly. This allows the model to preserve intent while reducing complexity.

**Summarized:**   
John: unstable internet (3 days), video issues

When to use?

- When readability is important
- Conversational systems
- Reporting or summaries

**3\. Token-level optimization**

Token-level optimization reduces the number of tokens processed by the model by simplifying expressions and removing unnecessary words.

This works by,

- Using abbreviations (e.g., “days” → “d”)
- Removing filler words
- Compacting phrases

Since LLM cost and latency are directly proportional to token usage, this step significantly improves efficiency.

**Optimized:**   
John: unstable internet, 3d, video issues

When to use?

- Cost-sensitive systems
- High-volume LLM usage
- Real-time applications

**4\. Selective context (query-aware compression)**  

Selective context ensures that only information relevant to a specific query is included. This works by evaluating the query and filtering out unrelated information, like how attention mechanisms prioritize relevant parts of input in LLMs.

Query: Which issue is urgent?   
**Filtered:**   
John: unstable internet, urgent

When to use?

- Question answering
- RAG systems
- Multi-query workflows

**5\. Context compression**

Context compression combines all techniques into a pipeline:

Original → Extract → Summarize → Optimize → Filter → Final

Token-level optimization (Optimize) and selective context (Filter) are integral parts of this pipeline.

This step-by-step transformation allows systems to progressively reduce input size while preserving essential information, making it easier to handle long-context inputs efficiently.

Why it matters?

- Enables handling of long context
- Improves scalability

## Advanced compression techniques

**1\. Embedding-based compression**

Embedding-based compression uses vector representations of text to identify semantically relevant information.

The input is converted into embeddings and similarity scores are used to retain only the most relevant segments. This is particularly useful in RAG systems where only relevant document chunks should be retrieved.

When to use?

- Large datasets
- Document-heavy systems
- RAG pipelines

**2\. Model-based prompt compressors**

Traditional techniques rely on predefined rules, which may not always capture deeper meaning. Model-based prompt compressors address this by using machine learning models to automatically compress prompts in a context-aware manner.

These models analyse the full prompt, identify important information and generate a shorter version while preserving meaning.

Example:   
Customer John reported unstable internet for 3 days with video issues

**Compressed:**   
John: unstable internet, 3d, video issues

Recent research from arxiv highlights techniques like LLMLingua, LLMLingua-2 and LongLLMLingua from Microsoft, which help compress prompts efficiently without losing meaning and improve LLM performance.

Why it matters?

- Understands context, not just keywords
- Works well with complex and long inputs

**3\. Data distillation**

Data distillation compresses large volumes of data into smaller, high-quality representations by removing redundancy and retaining core insights. Unlike prompt-level compression, this operates at a dataset level and is often used as a preprocessing step.

When to use?

- Large-scale enterprise data
- Preprocessing pipelines
- Training data optimization

**Prompt design considerations**

Hard prompt vs soft prompt

Prompt compression focuses on optimizing hard prompts, which are human-written text inputs.

- Hard prompt: Direct input text
- Soft prompt: Learned embeddings that guide model behaviour

While soft prompts modify how the model behaves internally, prompt compression improves efficiency by reducing the size and complexity of the input itself.

## Use case: Build a prompt compression assistant

Modern AI systems process long inputs such as conversations, logs and user queries. These inputs increase token usage and reduce efficiency.

Example input:

“Customer reported that the application has been crashing repeatedly for the past 3 days during file uploads, and this is blocking work”.

Compressing such inputs requires more than simple summarization. It involves:

- Identifying key information
- Removing redundant details
- Optimizing for token efficiency
- Preserving essential meaning

Manual compression is inconsistent and time-consuming. Automating this requires a structured multi-stage workflow, making it suitable for step-by-step reasoning.

## Objective

Build an AI assistant that,

- Extracts key details from long inputs
- Compresses content into concise prompts
- Preserves essential information
- Produces structured outputs

Each stage builds on the previous one, forming a prompt compression pipeline.

## Implementing prompt compression with watsonx orchestrate

Prompt compression can be implemented in watsonx Orchestrate by designing a structured workflow where each stage of compression is applied systematically.   
   
**Steps**

**Step 1:** Create the agent in watsonx Orchestrate

Before implementing prompt compression, we first create an AI agent using the watsonx Orchestrate agent builder interface.

Ensure that you have access to watsonx Orchestrate. You can sign in or register for an account through the watsonx platform. Once logged in, navigate to the watsonx Orchestrate console and open the Build agents and tools workspace. This interface provides a visual environment for defining agent capabilities, behaviour policies and knowledge sources without requiring application code. 

Select Create from scratch to initialise a new agent for the prompt compression use case.

In this example, the agent is configured to process long input prompts and transform them into concise, structured outputs by applying a multi-stage compression workflow.

Provide a descriptive name and purpose for the agent. 

Name: Customer Support Prompt Compression   
Description: It receives the input prompt (e.g; customer issue text) and processes it through multiple compression steps.

![watsonx Orchestrate - Build agents and tools - v2](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--71c5e3dc-81e9-4e5b-ab98-ebfdb637a1b2/watsonx-orchestrate-build-agents-and-tools-v2.png?preferwebp=true&width=1584 "IBM Orchestrate agent creation interface with prompt window")

![watsonx Orchestrate - Customer Support Prompt Compression - Profile](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--cf1144f1-3bbf-4d7f-8d31-e626908edb45/watsonx-orchestrate-customer-support-prompt-compression-profile.png?preferwebp=true&width=1584 "IBM watsonx Orchestrate customer support dashboard interface")

**Step 2:** Add sample data to the Knowledge layer

In watsonx Orchestrate Agent Builder, prompt compression examples and transformation patterns are supplied through the knowledge layer rather than traditional input variables.

After creating the agent, navigate to the Knowledge section in Agent Builder. The knowledge panel allows the agent to access external documents and example datasets during execution.

**How to add the dataset?**

To follow this tutorial,

1. Create a .txt file on your system
2. Copy and paste the dataset provided below into the file
3. In Agent Builder:
- Click Add source
- Select Upload files
- Upload the .txt file

Alternatively, you can paste the dataset directly if your interface supports manual input.

![watsonx Orchestrate - Customer Support Prompt Compression - Knowledge sources](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--f380085e-ac2f-43b6-9c88-b213eb027c71/watsonx-orchestrate-customer-support-prompt-compression-knowledge-sources.png?preferwebp=true&width=1584 "IBM watsonx Orchestrate dashboard with support prompt")

![watsonx Orchestrate - Customer Support Prompt Compression - Upload Files](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--30fb5199-f617-4ee2-8714-104ed325513b/watsonx-orchestrate-customer-support-prompt-compression-choose-knowledge-source-upload-files.png?preferwebp=true&width=1584 "IBM watsonx Orchestrate knowledge source selection screen")

![watsonx Orchestrate - Customer Support Prompt Compression - Add knowledge](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--3e0d7801-36f7-4e08-a0ce-164cf0fc0b51/watsonx-orchestrate-customer-support-prompt-compression-add-knowledge.png?preferwebp=true&width=1584 "IBM Watson Orchestrate add knowledge source interface")

During inference, watsonx Orchestrate retrieves semantically relevant examples from this knowledge source and injects them into the agent’s reasoning context. This design decouples data from prompt construction, improving maintainability and consistency.

**Sample data**

For this tutorial, we use a structured dataset representing prompt compression scenarios, where each record includes:

- A raw input prompt
- Key contextual details (entity, issue, duration, urgency)
- A compressed output

**Customer Support Compression Dataset**  

Example: 1  

Input: Customer John reported that his internet has been unstable for the past 3 days with frequent disconnections during video calls. He restarted the router twice, but the issue persists.

Extract: 

John: unstable internet, 3 days, video call issues, restart failed

Compressed Output:

Resolve issue: John unstable internet 3d restart failed

Example: 2  

Input: Customer Priya mentioned that her payment failed multiple times while booking tickets. The issue started yesterday and is urgent as tickets are limited.

Extract:  

Priya: payment failure, since yesterday, urgent

Compressed Output:

Resolve issue: Priya payment failure urgent

Example: 3  

Input: Customer Raj is facing slow application performance for the last week, especially during login. This is impacting his work.

Extract:

Raj: slow app, 1 week, login issue, work impacted

Compressed Output:

Resolve issue: Raj slow app 1w login issue

Example: 4  

Input: Customer Ankit reported that he cannot reset his password despite multiple attempts. This has been happening for 2 days.

Extract:

Ankit: password reset issue, 2 days

Compressed Output:

Resolve issue: Ankit password reset issue 2d

Example: 5  

Input: Customer Meena says the mobile app crashes every time she tries to upload a document. This issue started today and is blocking her work.

Extract:

Meena: app crash, document upload, today, blocking work

Compressed Output:

Resolve issue: Meena app crash upload blocking

**Configure the knowledge source**  

After uploading the file, provide a descriptive knowledge name and purpose:

Name: Customer Support Knowledge Base

Description: This knowledge base contains examples of customer support issues and their compressed versions.

It helps the agent:

- Extract key information such as customer name, issue, duration, and urgency
- Convert long customer queries into concise, token-efficient prompts
- Learn structured compression patterns from examples

Use this knowledge when processing customer support queries that need summarization, extraction or prompt compression.

The knowledge includes:

- Raw customer issue descriptions
- Extracted key information
- Final compressed outputs

This ensures consistent, accurate and optimised responses.

![watsonx Orchestrate - Customer Support Prompt Compression - Knowledge details](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--0b7a8381-be54-4d71-aed1-f083d7498327/watsonx-orchestrate-customer-support-prompt-compression-knowledge-details.png?preferwebp=true&width=1584 "IBM Watson Orchestrate knowledge source configuration screen")

This description helps watsonx Orchestrate determine when the knowledge should be used during reasoning.

**Supported knowledge sources**

Watsonx Orchestrate supports multiple knowledge backends, including:

- Databases for structured enterprise data
- Search systems such as,
1. Keyword search (e.g., Elasticsearch)
2. Vector search used in RAG pipelines for semantic retrieval

For this tutorial, we use Upload files which is suitable for controlled demonstrations and lightweight datasets.

Once saved, the dataset appears as an active knowledge source for the agent. At this stage, the agent can retrieve relevant examples dynamically during inference and apply consistent compression patterns.

![watsonx Orchestrate - Customer Support Prompt Compression - Knowleldge base](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--a6882686-4c19-4024-a456-6fe0b578b2d4/watsonx-orchestrate-customer-support-prompt-compression-knowledge-base.png?preferwebp=true&width=1584 "IBM watsonx Orchestrate agent setup interface screenshot")

**Step 3:** Implementing prompt compression and behaviour policies

With the agent created and prompt compression examples added through the Knowledge layer, the next step is to define how the agent performs compression using structured behaviour policies.

Define the compression workflow

The prompt compression process is designed as a sequence of stages:

Input   
   ↓   
Key detail extraction   
   ↓   
Concise summarisation   
   ↓   
Token optimisation   
   ↓   
Selective filtering   
   ↓   
Structured compressed output

Each stage represents a focused transformation that progressively reduces the input while preserving essential information.

**How is this workflow implemented in the agent?**

In watsonx Orchestrate, these stages are not configured as separate steps or nodes.

Instead, the entire workflow is implemented inside a single behaviour prompt. The pipeline defines what should happen conceptually, while the behaviour prompt defines how those stages are executed in practice. During execution, the model follows the behaviour instructions and internally performs each stage in sequence within a single interaction.

**Mapping the pipeline to the behaviour prompt**

The multi-stage compression pipeline is implemented directly within the behaviour prompt as a sequence of structured instructions. Each stage including key detail extraction, concise summarisation, token optimisation, selective filtering and structured output, is defined as a step in the prompt.

When the agent processes an input, the model follows these instructions in order and performs each transformation internally. This ensures that the conceptual pipeline is executed consistently within a single interaction.

**Defining compression policies using the Behaviour section**

Navigate to the Behaviour section in Agent Builder.

The Behaviour section defines persistent rules that guide how the agent interprets input and generates output. Unlike one-time prompts, behaviour policies apply consistently across interactions, ensuring structured reasoning and predictable outputs.

For prompt compression workflows, this ensures that the agent,

- Preserves essential information rather than over-compressing
- Removes redundant or low-value details
- Produces concise and consistent outputs
- Handles incomplete or unclear input predictably

**Behaviour prompt**

You are a prompt compression assistant for customer support. Your goal is to reduce input text into a short, token-efficient prompt while preserving only critical information.

Follow these steps strictly:

Step 1: Extract

- Customer name
- Core issue
- Duration (if available)
- Urgency (if available)

Step 2: Summarize

- Convert extracted information into a short phrase

Step 3: Optimize

- Minimize words
- Use abbreviations (e.g., days → d, week → w)
- Remove filler words

Step 4: Filter (VERY IMPORTANT)

Remove non-essential details such as,

- number of contacts
- repeated actions
- background explanations
- unnecessary context
- Keep only information required to understand and resolve the issue

Step 5: Output

Return ONLY:

Resolve issue: <compressed text>

Rules:

- Maximum 10–15 words
- Do NOT include explanations
- Do NOT include extra details
- Do NOT repeat information
- Always prioritize brevity over completeness

Example:

Input: Customer John reported internet issues for 3 days and contacted support twice.

Output: Resolve issue: John internet issue 3d

This behaviour policy ensures that the agent applies the same compression logic consistently, regardless of the input source. By embedding the pipeline directly into the behaviour prompt, the agent performs structured, multi-stage compression within a single interaction, making the workflow both simple to configure and effective in practice.

![watsonx Orchestrate - Customer Support Prompt Compression - Behavior](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--95ef7c96-0da7-4963-8983-bd588b3ec277/watsonx-orchestrate-customer-support-prompt-compression-behavior.png?preferwebp=true&width=1584 "IBM watsonx Orchestrate Customer Support Interface Screenshot")

**Step 4:** Execute the prompt compression workflow

After configuring the agent, behaviour policies, and knowledge layer, the next step is to execute the prompt compression workflow using the agent interaction panel. 

Navigate to the Talk to agent panel in the watsonx Orchestrate interface.

Enter a sample input prompt in the interaction window. For example, 

Paste this input into the agent and submit the query.

Test case: 1  

Customer Arjun reports that his order has not been delivered even after 5 days. He contacted support twice but received no response. This is urgent.

Resolve issue: Arjun order not delivered 5d urgent 

Test case: 2

Customer Priya is facing payment failures while booking tickets since yesterday. She tried multiple times, but the issue persists and is urgent. 

Resolve issue: Priya payment failure 1d urgent

Test case: 3 

Customer Rahul reports that the mobile app crashes every time he tries to upload documents for the past 2 days, blocking his work.

Resolve issue: Rahul app crash uploading docs2d 

![watsonx Orchestrate - Customer Support Prompt Compression - Talk to agent](https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=320 640w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=384 768w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=512 1024w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=640 1280w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=768 1536w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=960 1920w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=1024 2048w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=1152 2304w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=1280 2560w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=1536 3072w,https://www.ibm.com/adobe/dynamicmedia/deliver/dm-aid--9f5a0cc2-239f-404d-a6d3-a9bf7ebc3af9/watsonx-orchestrate-customer-support-prompt-compression-behavior-talk-to-agent.png?preferwebp=true&width=1584 "IBM Watson Orchestrate Customer Support Console Interface")

When the input is submitted, the agent applies the defined behaviour and retrieves relevant patterns from the knowledge layer. It extracts key details, removes redundant information and compresses the prompt into a concise, structured output. The final response is optimized for minimal token usage while preserving essential information.

## Conclusion

Prompt compression is a critical optimization strategy for modern AI systems. By reducing prompt length and retaining only essential information, it enables more efficient use of context windows, improves response performance and lowers operational costs.

When implemented using IBM watsonx Orchestrate, this approach becomes even more effective. The structured workflow allows for modular design, where each stage of compression can be consistently applied and reused across different use cases. It also improves observability, making it easier to understand and debug how inputs are transformed at each stage. In addition, prompt compression supports scalability by working across diverse domains such as customer support, finance and healthcare, while ensuring cost optimization through reduced token usage before LLM inference. 

Together, these capabilities make prompt compression a practical and powerful technique for building efficient, scalable and production-ready AI systems.