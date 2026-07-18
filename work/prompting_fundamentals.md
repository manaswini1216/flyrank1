# Prompting Fundamentals on Real Tasks

## Target Task

Technical interview preparation.

---

# Version 0 - Naive Prompt

## Technique

None

## Prompt

Help me prepare for a Java interview.

## Output (excerpt)

General Java interview topics such as OOP, collections, exceptions, and multithreading.

## Notes

The response was generic and lacked structure.

---

# Version 1 - Role Assignment

## Prompt

Act as a senior Java interviewer. Help me prepare for a Java interview.

## Output (excerpt)

The response became more interview-focused and asked technical questions.

## Notes

Role assignment made the answers more realistic.

---

# Version 2 - Context and Motivation

## Prompt

Act as a senior Java interviewer. I am preparing for an on-campus software engineering interview. Help me prepare by focusing on the most commonly asked Java topics.

## Output (excerpt)

The response focused on interview-relevant concepts instead of broad Java theory.

## Notes

Adding context made the answers more relevant.

---

# Version 3 - Few-shot Examples

## Prompt

Act as a senior Java interviewer.

Example:

Question:
What is polymorphism?

Answer:
Polymorphism allows one interface to represent different implementations.

Now continue asking similar interview questions.

## Output (excerpt)

The generated questions followed the same interview style.

## Notes

The examples improved consistency.

---

# Version 4 - Output Structure

## Prompt

Act as a senior Java interviewer.

Present every answer as:

Question

Expected Answer

Common Mistakes

Follow-up Question

## Output (excerpt)

The responses became easier to study.

## Notes

The structured format improved readability.

---

# Version 5 - Step Decomposition

## Prompt

Act as a senior Java interviewer.

Start with Core Java.

After finishing, move to Collections.

Then Exceptions.

Then Multithreading.

Finally ask five mock interview questions.

## Output (excerpt)

The preparation became organized into a learning sequence.

## Notes

Breaking the task into steps produced a more complete study guide.

---

# Claude vs ChatGPT

## Claude

More detailed explanations and better reasoning.

## ChatGPT

More concise responses with clearer formatting.

## Failure Points

Claude sometimes produced longer explanations than necessary.

ChatGPT occasionally skipped deeper implementation details.

---

# Final Prompt Template

Act as a senior interviewer for the specified role.

Context:
{candidate_background}

Goal:
{goal}

Use this structure:

1. Explain the topic.

2. Give one interview question.

3. Give the expected answer.

4. Mention common mistakes.

5. Ask one follow-up question.

Keep explanations practical and interview-focused.
