# @adaline/xai

## 1.5.0

### Minor Changes

- c4b114e: Add the latest provider models (researched 2026-07-10 from official docs, pricing, and deprecation pages).

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

## 1.4.0

### Minor Changes

- 6209467: Remove models the providers no longer serve, per official deprecation/retirement pages (retrieved 2026-07-10).

  BREAKING (for consumers pinning these literals or importing their classes):

  - Anthropic: all Claude 3.x models and the Claude 4 20250514 snapshots (9 models, retired on the first-party API).
  - Google: the Gemini 1.5 and 2.0 families, `text-embedding-004`, `text-embedding-001` (13 models removed); the retired 2.5/3 preview models are unregistered from routing but their schemas remain exported for `@adaline/vertex` (4 models).
  - Vertex: the Gemini 1.5 and 2.0 families, `text-embedding-004`, `textembedding-gecko@003`, `textembedding-gecko-multilingual@001` (14 models).
  - Azure OpenAI: the GPT-3.5/GPT-4 legacy family and retired chat aliases (`gpt-5-chat-latest`, `gpt-5.2-chat-latest`, `chatgpt-5.2`, `chatgpt-4o-latest`) (13 models).
  - Bedrock: `anthropic.claude-3-opus-20240229-v1:0`, `anthropic.claude-opus-4-20250514-v1:0`.
  - Groq: `gemma2-9b-it`, `deepseek-r1-distill-llama-70b`, `moonshotai/kimi-k2-instruct(-0905)`, `meta-llama/llama-4-maverick-17b-128e-instruct`, `meta-llama/llama-guard-4-12b`.
  - xAI: the entire previous catalog (grok-2/grok-3/grok-4/grok-4.1-fast families and `grok-code-fast-1`, 14 models retired by xAI on 2026-05-15). Replacement models land in the follow-up release.

  Also:

  - Sweeps orphan pricing-only keys with no model files across google, vertex, groq, xai, and anthropic.
  - Vertex: `text-multilingual-embedding-002` had a model file but was never registered with the provider; now routable.
  - Bedrock: legacy models still served (Claude 3 Haiku/Sonnet, 3.5 Sonnet v1+v2, 3.7 Sonnet, Sonnet 4) are annotated with their AWS EOL dates.

## 1.3.6

### Patch Changes

- Updated dependencies [ab5f7df]
  - @adaline/provider@1.10.5
  - @adaline/types@1.15.1

## 1.3.5

### Patch Changes

- Updated dependencies [4f55295]
  - @adaline/types@1.15.0
  - @adaline/provider@1.10.4

## 1.3.4

### Patch Changes

- 48702e8: Fix top dependabot vulnerabilities
- Updated dependencies [48702e8]
  - @adaline/provider@1.10.3
  - @adaline/types@1.14.1

## 1.3.3

### Patch Changes

- 5b21690: Remove the redundant 'type' union on 'search-result' modality, not a discriminanted union anynmore
- Updated dependencies [5b21690]
  - @adaline/types@1.14.0
  - @adaline/provider@1.10.2

## 1.3.2

### Patch Changes

- Updated dependencies [3cab885]
  - @adaline/types@1.13.0
  - @adaline/provider@1.10.1

## 1.3.1

### Patch Changes

- e98e85e: bump rollup to >=4.59.0 to resolve CVE (Arbitrary File Write via Path Traversal)

## 1.3.0

### Minor Changes

- ba6ea54: Implement retry with delay (response based) + jitter in case of 429 errors

### Patch Changes

- Updated dependencies [ba6ea54]
  - @adaline/provider@1.10.0

## 1.2.0

### Minor Changes

- f50ecbb: add thoughtsignature

### Patch Changes

- Updated dependencies [f50ecbb]
  - @adaline/provider@1.9.0
  - @adaline/types@1.12.0

## 1.1.0

### Minor Changes

- b90c856: Add xAI/Grok provider with support for 17 Grok models
