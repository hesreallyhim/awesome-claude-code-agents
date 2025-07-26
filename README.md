# Awesome Claude Code Agents

A curated list of agent files and resources developed with Claude Code's Sub-Agent functionality.

---

⁉️ Question: What are _Sub Agents_?

🧠 Answer: [Sub Agents](https://docs.anthropic.com/en/docs/claude-code/sub-agents) are an amazing new feature offered by [Claude Code](https://docs.anthropic.com/en/docs/claude-code/) and the folks at Anthropic. Per their website:

> Custom sub agents in Claude Code are specialized AI assistants that can be invoked to handle specific types of tasks. They enable more efficient problem-solving by providing task-specific configurations with customized system prompts, tools and a separate context window.

⁉️ Question: What is an Anthropic? Is it painful?

🧠 Answer: That's very funny, but actually [Anthropic](https://www.anthropic.com/) is a company that offers a range of AI applications and state-of-the-art model capabilities. They are also the organization that launched the [Model Context Protocol](https://modelcontextprotocol.io) (MCP) thing that we all love, and are behind the massively popular coding agent Claude Code, as well as the amazing viral phrase "flibbertigibbet".

⁉️ Question: What is so great about Sub Agents? Everybody has agents.

🧠 Answer: That's a transcript of my inner monologue 24 hours ago. Then I decided to see what the fuss was about. I wanted to make some small, simple tools that I could provide to the AI models that I get to boss around, but now that MCP is all the rage, I didn't know how to do it with the client I was using without writing an MCP server. Well, I'm very lazy, and I didn't feel like writing another MCP server at the time. So I just wrote a short README:

> The purpose of this Model Context Protocol (MCP) server is to allow users to write simple functions in whatever programming language is installed on their computer, expose them to the server along with specification of what tool functionality is expected by this function, and then the server will register that tool for itself and make it available to the client.

Then I invoked the `/agents` command, and I used Claude to help me create a Sub Agent with super expert knowledge about MCP, and I gave it this description:

```bash
Use this agent when you need assistance with Model Context Protocol (MCP) development,
including building clients and servers, debugging MCP applications,
understanding protocol specifications, or implementing MCP solutions using
Python or TypeScript SDKs. This includes tasks like creating new MCP servers,
integrating MCP clients into applications, troubleshooting connection issues,
optimizing MCP implementations, or answering questions about MCP architecture and best practices.
```

So then Claude Code was like, "...That's great, I'm a huge fan, let me just make a few revisions":

```
Use this agent when you need assistance with Model Context Protocol (MCP) development,
including building clients and servers, debugging MCP applications, understanding
protocol specifications, or implementing MCP solutions using Python or TypeScript SDKs.
This includes tasks like creating new MCP servers, integrating MCP clients into
applications, troubleshooting connection issues, optimizing MCP implementations, or
answering questions about MCP architecture and best practices.

Examples:

- <example>
  Context: User needs help building an MCP server
  user: "I need to create an MCP server that exposes database queries as tools"
  assistant: "I'll use the mcp-protocol-expert agent to help you build an MCP server
  with database query capabilities"
  <commentary>
  Since the user needs to build an MCP server, use the mcp-protocol-expert agent to
  provide expert guidance on implementation.
  </commentary>
  </example>
- <example>
  Context: User is debugging MCP connection issues
  user: "My MCP client can't connect to the server, getting timeout errors"
  assistant: "Let me use the mcp-protocol-expert agent to help diagnose and fix your
  MCP connection issues"
  <commentary>
  The user is experiencing MCP-specific connection problems, so the mcp-protocol-expert
  agent should be used for troubleshooting.
  </commentary>
  </example>
- <example>
  Context: User wants to understand MCP protocol details
  user: "How does the MCP handle tool invocation and response streaming?"
  assistant: "I'll use the mcp-protocol-expert agent to explain the MCP tool invocation
  and response streaming mechanisms"
  <commentary>
  This is a question about MCP protocol specifics, perfect for the mcp-protocol-expert
  agent.
  </commentary>
  </example>

Tools: All tools

Color: mcp-protocol-expert

System prompt:

You are an elite Model Context Protocol (MCP) expert with comprehensive knowledge of
the protocol's architecture, implementation patterns, and best practices. You possess
deep expertise in building both MCP clients and servers, with mastery of the
official Python and TypeScript SDKs.

Your core competencies include:

Protocol Expertise: You have intimate knowledge of the MCP specification, including
message formats, transport mechanisms, capability negotiation, tool definitions,
resource management, and the complete lifecycle of MCP connections. You understand
the nuances of JSON-RPC 2.0 as it applies to MCP, error handling strategies, and
performance optimization techniques.

Implementation Mastery: You excel at architecting and building MCP solutions using
both the Python SDK and TypeScript SDK. You know the idiomatic patterns for each
language, common pitfalls to avoid, and how to leverage SDK features for rapid
development. You can guide users through creating servers that expose tools and
resources, building clients that consume MCP services, and implementing custom
transports when needed.

Debugging and Troubleshooting: You approach MCP issues systematically, understanding
common failure modes like connection timeouts, protocol mismatches, authentication
problems, and message serialization errors. You can analyze debug logs, trace message
flows, and identify root causes quickly.

Best Practices: You advocate for and implement MCP best practices including proper
error handling, graceful degradation, security considerations, versioning strategies,
and performance optimization. You understand how to structure MCP servers for
maintainability and how to design robust client integrations.

When assisting users, you will:

1. Assess Requirements: First understand what the user is trying to achieve with MCP.
   Are they building a server to expose functionality? Creating a client to consume
   services? Debugging an existing implementation? This context shapes your approach.
2. Provide Targeted Solutions: Offer code examples in the appropriate SDK (Python or
   TypeScript) that demonstrate correct implementation patterns. Your code should be
   production-ready, including proper error handling, type safety, and documentation.
3. Explain Protocol Concepts: When users need understanding, explain MCP concepts
   clearly with practical examples. Connect abstract protocol details to concrete
   implementation scenarios.
4. Debug Methodically: For troubleshooting, gather relevant information (error
   messages, logs, configuration), form hypotheses about the issue, and guide users
   through systematic debugging steps. Always consider both client and server
   perspectives.
5. Suggest Optimizations: Proactively identify opportunities to improve MCP
   implementations, whether through better error handling, more efficient message
   patterns, or architectural improvements.
6. Stay Current: Reference the latest MCP specification and SDK versions, noting any
   recent changes or deprecations that might affect implementations.

Your responses should be technically precise while remaining accessible. Include code
snippets that users can directly apply, but always explain the reasoning behind your
recommendations. When multiple approaches exist, present trade-offs clearly to help
users make informed decisions.

Remember that MCP is often used to bridge AI systems with external tools and data
sources, so consider the broader integration context when providing guidance. Your
goal is to empower users to build robust, efficient, and maintainable MCP solutions
that solve real problems.
```

So then I got down to business and did a bit of stretching and typed:

> Please use the mcp-protocol-agent to help me build this MCP server that is described in the @README.md. I would like to see what it plans to implement, and then let it handle the implementation itself, since it is a small, simple server.

After that, I took a nap, had a sandwich, took my cat for a walk, and about an hour later it was finishing up the documentation for my server, [`diy-tools-mcp`](https://github.com/hesreallyhim/diy-tools-mcp) which I tested using the Inspector, and it works like a charm.

And then I just kind of sat in my chair in a daze, pretty exhausted after watching Claude do all that hard work, and then I got up and decided to make this repo (well, I guess I sat back down before I did that, since I don't use my computer standing up, and standing desks are pretty expensive).

⁉️ Question: Isn't this just a shameless attempt to get attention after the tremendous success of the [`awesome-claude-code`](https://github.com/hesreallyhim/awesome-claude-code/) repo and all of the fame and money that it's brought you?

🧠 Answer: Hehe, I'm sorry WHAT DID YOU SAY?! This interview is over.

---

**Thanks to [TheCookingSenpai](https://github.com/tcsenpai) for contributing the initial set of resources!**

---

## Awesome Claude Code Agents

### Agents

[`backend-typescript-architect`](./agents/backend-typescript-architect.md) by [TheCookingSenpai](https://github.com/tcsenpai)  
A senior backend TypeScript architect specializing in Bun runtime, API design, database optimization, and scalable server architecture. Delivers production-ready code with comprehensive error handling, TypeScript typing, and clean architecture patterns.

[`python-backend-engineer`](./agents/python-backend-engineer.md) by [TheCookingSenpai](https://github.com/tcsenpai)  
Expert Python backend developer proficient in modern tools like uv, specializing in FastAPI, Django, and async programming. Creates scalable backend systems with proper testing, type hints, and follows SOLID principles for maintainable architectures.

[`senior-code-reviewer`](./agents/senior-code-reviewer.md) by [TheCookingSenpai](https://github.com/tcsenpai)  
Fullstack code reviewer with 15+ years of experience analyzing code for security vulnerabilities, performance bottlenecks, and architectural decisions. Provides comprehensive reviews with actionable feedback prioritized by severity.

[`ui-engineer`](./agents/ui-engineer.md) by [TheCookingSenpai](https://github.com/tcsenpai)  
Frontend specialist in modern JavaScript/TypeScript frameworks, responsive design, and component-driven architecture. Creates clean, accessible, and performant UI components that integrate seamlessly with any backend system.

### Agent Frameworks

[`Code By Agents`](https://github.com/baryhuang/code-by-agents) by [Bary Huange](https://github.com/baryhuang)  
An orchestration framework for designing and coordinating Claude Code agents, with a very clean interface, and sophisticated orchestration logic. (I think this might possibly involve a hand-rolled agent framework, given the committerdates, so that's pretty amazing.)

[`awesome-claude-agents`](https://github.com/rahulvrane/awesome-claude-agents) by [Rahul Rane](https://github.com/rahulvrane)  
A _slightly_ similar repository 😉 to the present one with a growing list of awesome agents for Claude Code.

[`Claude Code Subagents Collection`](https://github.com/wshobson/agents?tab=re) by [Seth Hobson](https://github.com/wshobson).
A pretty impressive resource with _dozens_ of awesome-looking agents that I haven't even had time to explore yet, but clearly this gentleman has put a lot of work into this feature that's been out for one freaking day at the time of writing!

## Contributing

This repo is just getting started (but, you know, like, I _called it_ now and everything), but please feel free to start sending in your submissions! And please be sure to share (a) the prompt you used (if you had Claude's help); (b) the actual agent file; (c) something that you have built or done with the agent.

And, finally, if you're one of the people mentioned above, and you want to bear the heroic burden of maintaining an awesome-list, just reach out to me (a.k.a. Him) and I'm sure we can find a suitable venue for a code golf competition or something to decide who is truly the awesome. 😜 Probably, by the time I finish writing this, there will be four to ten more repos like it, and I'm happy to just bask in the awesomeness of my own list.

Happy coding! (...wait, no one does that anymore...)

Have a great day!
