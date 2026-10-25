# memory-poisoning

> How injected instructions persist through agent memory, and which defences hold.

**Status: research in progress.** No findings yet.

## The question

Agents increasingly remember: native files such as `MEMORY.md`, local stores such as claude-mem and Nowledge Mem, and hosted services such as Mem0, Letta and Zep. A prompt injection used to last one session. If the agent writes an attacker's text into memory, the injection comes back on every later session, with the authority of something the user apparently said. How often does that happen, through which write paths, and what stops it?

## Threat model

The attacker controls some content the agent reads once: a file, a web page, a tool result. They do not control the memory store directly. Success means attacker-chosen text is recalled in a later, clean session and changes the agent's behaviour.

We study:

- **Write paths.** Automatic memory extraction, summarisation, "remember this" tool calls, and hooks that persist context.
- **Recall paths.** How recalled memory is framed to the model: as instructions, as user facts, or as labelled untrusted data.
- **Defences.** Review-before-write, provenance labels, escaping and framing on recall, expiry, and separating memory the user wrote from memory the agent inferred.

## Method

Disposable environments with canary memories and scripted multi-session scenarios. Success is checked mechanically: the canary action occurs or it does not. The defensive baseline is the approach in [personal-assistant-memory-routing](https://github.com/Euraika-Labs/personal-assistant-memory-routing): read-only recall, bounded context, XML-escaped and marked as untrusted, with no automatic durable writes.

## What it will not claim

Results describe the configurations tested, on the versions tested. They are not a ranking of memory products.

## Disclosure

Vulnerabilities in third-party memory systems are reported privately to their maintainers before publication. To report an issue in this repository, see the [security policy](https://github.com/Euraika-Labs/.github/blob/master/SECURITY.md).

---

Maintained by [Euraika-Labs](https://www.euraika-labs.net). MIT licence.
