# repr-llm

Create lightweight representations of objects for Large Language Model consumption

## Background

While experimenting with Large Language Models directly [💬](https://platform.openai.com/docs/api-reference/chat/create) [🤗](https://huggingface.co/) and with tools like [genai](https://github.com/noteable-io/genai), [dangermode](https://github.com/rgbkrk/dangermode), and [langchain](https://github.com/hwchase17/langchain) I've been naturally converting representations of my data or text to markdown as a format that GPT models can understand and converse with a user about.

Some of the core limitations for Large Language Models are:

* Length of inputs -- limited by # of tokens it can accept  or $$
* What can you send it in a safe manner (what data fields, 🚫 secrets)

What I'd like to have library authors do, similar to what we did with `_repr_html_` for notebook and ipython use is `_repr_llm_` to create a lightweight representation of objects that is:

* Deterministic - no side effects
* Navigable - states what other functions can be run to inquire about data
* Lightweight - take into account how much text a GPT model can read

## TODO

* Talk about how ChatGPT plugins built with FastAPI provide something very similar with the `api_plugin_json` and OpenAPI specs, especially since there's a delineation of `description_for_human` and `description_for_model`.
* Demonstrate how `genai` currently creates a summarized DataFrame
* Show some object examples, comparing between the current `_repr_markdown_` approach and the `_repr_llm_` approach

## Credit

Originally I was going to suggest more package authors use `_repr_markdown_` (and they should!). Then [Peter Wang](https://github.com/pzwang) suggested that we have a version written for the machine, just like `ai-plugin.json` does, especially since the LLMs _can_ be a more advanced reader.

Thank you to [Dave Shoup](https://github.com/shouples) for the conversations about pandas representation and how we can keep improving what we send for `Out[*]` to Large Language Models.
