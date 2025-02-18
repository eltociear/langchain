Welcome to LangChain
==========================

Large language models (LLMs) are emerging as a transformative technology, enabling
developers to build applications that they previously could not.
But using these LLMs in isolation is often not enough to
create a truly powerful app - the real power comes when you are able to
combine them with other sources of computation or knowledge.

This library is aimed at assisting in the development of those types of applications.

There are five main areas that LangChain is designed to help with.
These are, in increasing order of complexity:

1. LLM and Prompts
2. Chains
3. Data Augmented Generation
4. Agents
5. Memory

Let's go through these categories and for each one identify key concepts (to clarify terminology) as well as the problems in this area LangChain helps solve.

**🦜 LLMs and Prompts**

Calling out to an LLM once is pretty easy, with most of them being behind well documented APIs.
However, there are still some challenges going from that to an application running in production that LangChain attempts to address.

*Key Concepts*

- LLM: A large language model, in particular a text-to-text model.
- Prompt: The input to a language model. Typically this is not simply a hardcoded string but rather a combination of a template, some examples, and user input.
- Prompt Template: An object responsible for constructing the final prompt to pass to a LLM.

*Problems Solved*

- Switching costs: by exposing a standard interface for all the top LLM providers, LangChain makes it easy to switch from one provider to another, whether it be for production use cases or just for testing stuff out.
- Prompt management: managing your prompts is easy when you only have one simple one, but can get tricky when you have a bunch or when they start to get more complex. LangChain provides a standard way for storing, constructing, and referencing prompts.
- Prompt optimization: despite the underlying models getting better and better, there is still currently a need for carefully constructing prompts.

**🔗️ Chains**

Using an LLM in isolation is fine for some simple applications, but many more complex ones require chaining LLMs - either with eachother or with other experts.
LangChain provides several parts to help with that.

*Key Concepts*

- Tools: APIs designed for assisting with a particular use case (search, databases, Python REPL, etc). Prompt templates, LLMs, and chains can also be considered tools.
- Chains: A combination of multiple tools in a deterministic manner.

*Problems Solved*

- Standard interface for working with Chains
- Easy way to construct chains of LLMs
- Lots of integrations with other tools that you may want to use in conjunction with LLMs
- End-to-end chains for common workflows (database question/answer, api calling, etc)

**📚 Data Augmented Generation**

LLMs have access to all the data they were trained on, but there are still large chunks of data they were not trained on.
Data Augmented Generation covers how to use LLMs to generate text conditioning on data outside of what the LLM was trained on.

*Key Concepts*

- Documents: A document is a piece of text, along with some associated metadata, that can be inserted into the context of a query to condition generation on that text.
- Embeddings: A vector representation of text (or other unstructured data). Useful for being able to numerically compare pieces of text.
- Vectorstore: A database which stores embeddings and can be searched over.

*Problems Solved*

- Standard interface for working with Documents, Embeddings, and Vectorstores
- Lots of integrations with common embedding providers and vectorstores
- End-to-end chains for common workflows (recursive summarization, question answering over documents, etc)


**🤖 Agents**

Some applications will require not just a predetermined chain of calls to LLMs/other tools, but potentially an unknown chain that depends on the user input.
In these types of chains, there is a “agent” which has access to a suite of tools.
Depending on the user input, the agent can then decide which, if any, of these tools to call.

*Key Concepts*

- Tools: same as above.
- Agent: An LLM-powered class responsible for determining which tools to use and in what order.


*Problems Solved*

- Standard agent interfaces
- A selection of powerful agents to choose from
- Common chains that can be used as tools

**🧠 Memory**

By default, Chains and Agents are stateless, meaning that they treat each incoming query independently.
In some applications (chatbots being a GREAT example) it is highly important to remember previous interactions,
both at a short term but also at a long term level. The concept of "Memory" exists to do exactly that.

*Key Concepts*

- Memory: A class that can be added to an Agent or Chain to (1) pull in memory variables before calling that chain/agent, and (2) create new memories after the chain/agent finishes.
- Memory Variables: Variables returned from a Memory class, to be passed into the chain/agent along with the user input.

*Problems Solved*

- Standard memory interfaces
- A collection of common memory implementations to choose from
- Common chains/agents that use memory (e.g. chatbots)

Documentation Structure
=======================
The documentation is structured into the following sections:


.. toctree::
   :maxdepth: 1
   :caption: Getting Started
   :name: getting_started

   getting_started/installation.md
   getting_started/environment.md
   getting_started/llm.md
   getting_started/llm_chain.md
   getting_started/sequential_chains.ipynb
   getting_started/data_augmented_generation.ipynb
   getting_started/agents.ipynb
   getting_started/memory.ipynb

Goes over a simple walk through and tutorial for getting started setting up a simple chain that generates a company name based on what the company makes.
Covers installation, environment set up, calling LLMs, and using prompts.
Start here if you haven't used LangChain before.


.. toctree::
   :maxdepth: 1
   :caption: How-To Examples
   :name: examples

   examples/prompts.rst
   examples/chains.rst
   examples/data_augmented_generation.rst
   examples/agents.rst
   examples/memory.rst
   examples/model_laboratory.ipynb

More elaborate examples and walkthroughs of particular
integrations and use cases. This is the place to look if you have questions
about how to integrate certain pieces, or if you want to find examples of
common tasks or cool demos.


.. toctree::
   :maxdepth: 1
   :caption: Reference
   :name: reference

   reference/installation.md
   reference/integrations.md
   reference/prompts.rst
   reference/chains.rst
   reference/data_augmented_generation.rst
   reference/modules/agents


Full API documentation. This is the place to look if you want to
see detailed information about the various classes, methods, and APIs.


.. toctree::
   :maxdepth: 1
   :caption: Resources
   :name: resources

   explanation/core_concepts.md
   explanation/combine_docs.md
   explanation/agents.md
   explanation/tools.md
   explanation/glossary.md
   explanation/cool_demos.md
   Discord <https://discord.gg/6adMQxSpJS>

Higher level, conceptual explanations of the LangChain components.
This is the place to go if you want to increase your high level understanding
of the problems LangChain is solving, and how we decided to go about do so.

