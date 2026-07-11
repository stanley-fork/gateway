---
"@adaline/openai": patch
"@adaline/anthropic": patch
"@adaline/google": patch
"@adaline/vertex": patch
"@adaline/azure": patch
"@adaline/bedrock": minor
"@adaline/groq": patch
"@adaline/xai": minor
---

Add the latest provider models (researched 2026-07-10 from official docs, pricing, and deprecation pages).

Added:

- OpenAI: `gpt-5.6-sol`, `gpt-5.6-terra` (tiered pricing @272k), `gpt-5.6-luna`, with new `reasoning_effort: xhigh` and `reasoning_mode: standard|pro` config support (reasoningMode routes via the Responses API; the gpt-5.6 web-search bundle is default-deny on live web access).
- Anthropic: `claude-sonnet-5` (1M context, 128K output).
- Azure OpenAI: `gpt-5.4`, `gpt-5.4-mini`, `gpt-5.4-nano`, `gpt-5.4-pro`, `gpt-5.5`, `gpt-5-pro`, `o3-pro`, `gpt-5.6-sol`, `gpt-5.6-terra`, `gpt-5.6-luna`.
- Bedrock: `anthropic.claude-sonnet-5`, `anthropic.claude-opus-4-8`.
- Vertex: `gemini-3.5-flash`, `gemini-3.1-flash-lite`.
- Groq: `qwen/qwen3.6-27b`, `meta-llama/llama-prompt-guard-2-86m`, `meta-llama/llama-prompt-guard-2-22m`.
- xAI: `grok-4.5`, `grok-4.3`, `grok-4.20-0309-reasoning`, `grok-4.20-0309-non-reasoning`, `grok-4.20-multi-agent-0309`, `grok-build-0.1` — the replacement catalog for the models retired in the previous release.

Fixed:

- Bedrock (minor): corrected model IDs `anthropic.claude-opus-4-7-v1` → `anthropic.claude-opus-4-7` and `anthropic.claude-sonnet-4-6-v1` → `anthropic.claude-sonnet-4-6` (old IDs were never served), plus wrong 200K context limits (now 1M per AWS model cards).
- OpenAI: `chatgpt-5.2` was missing its pricing entry, so runtime cost lookup threw.
- Google: `gemini-2.5-pro` pricing is now context-tiered @200k; `gemini-embedding-2` corrected to $0.20/M.
- xAI (minor): request schema narrows `reasoning_effort` to the documented values (`none`, `low`).
- Deprecation notes added to descriptions of deprecated-but-live models across OpenAI, Google, and Groq (notably `gemini-embedding-001` shuts down 2026-07-14).
