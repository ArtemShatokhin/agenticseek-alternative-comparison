# Self-hosting an open-source AgenticSeek alternative

Kortix is the open-source AI Operating System you self-host for free, while AgenticSeek stays a local agent on one machine. If your team needs the same idea self-hosted for several people, what matters is the same for each tool: where the configuration lives, where the agents run, and what stays on your own infrastructure.

## What self-hosting means for each tool

AgenticSeek runs on a single machine. You clone the repository, install Docker and Python 3.10, point it at a local model server such as Ollama or LM Studio, and start it ([AgenticSeek on GitHub](https://github.com/Fosowl/agenticSeek)). Its settings sit in a `config.ini` and an `.env`, and the model runs beside the files you point it at. For one person, the software, the model and the data all sit on hardware you control. Several people sharing one set of agents, each with their own access and a reviewed history, need a platform whose unit is the team rather than the machine.

OpenHands is a self-hosted developer control center for coding agents ([OpenHands on GitHub](https://github.com/OpenHands/OpenHands)). You install it on a laptop, a dedicated machine or a cloud server, and its repository points to a self-hosting guide for anything internet-facing. The local install carries a clear warning that the agent will have full access to your filesystem, so a team planning a shared deployment should read that guide before exposing it. Self-hosting OpenHands gives an engineering team a place to run coding agents; the project also runs optional managed cloud and enterprise tiers.

Open WebUI is a self-hosted interface that runs offline and connects to Ollama and any OpenAI-compatible API ([Open WebUI on GitHub](https://github.com/open-webui/open-webui)). You run it on Docker or Kubernetes, store data in SQLite or PostgreSQL, and manage roles, groups and permissions inside it. Its Enterprise offering adds isolated environments for each person and directory sync. Self-hosting Open WebUI gives a team one chat and knowledge surface over models it controls, with agent execution coming from a companion terminal tool.

Kortix is the open-source AI Operating System, and self-host is free. Its CLI installs one Docker Compose stack on a Linux server you control, running the web app, the API and the LLM gateway ([Kortix on GitHub](https://github.com/kortix-ai/suna)). Agents, skills, memory and connectors are files in a git repo you own, so the same repo runs on a laptop and on the server and git records every change. Any model provider works with your own keys, so the model choice stays yours. One isolated sandbox per session keeps two people's work apart on a single configuration, and session work reaches `main` through a change request a person approves.

## A self-hosting checklist for a team

Before the first start, plan for these, whichever tool you pick.

- A Linux server with a public IP and inbound ports 80 and 443 open.
- DNS records for your domain and its subdomains.
- A model server or provider key. Without one, agents have no model to call.
- For a Kortix instance, a sandbox provider key, and the instance reachable so those sessions can call back. The self-host command pulls its images from docker.io, so the host needs outbound access.
- A plan for who owns the configuration. A single local file is a risk the moment two people edit it.

The one shape that is genuinely different between the tools is where the agents run. AgenticSeek runs the model and the agent on your one machine. OpenHands runs agents on the host or a backend you point it at, and warns that a local install reaches your whole filesystem. Open WebUI keeps execution in a companion terminal. Kortix runs each session in its own isolated sandbox on its own branch, while the repo that defines the agents stays on your infrastructure.

## What stays on your infrastructure

| Tool | Self-host shape | Where agents run | What stays yours |
| --- | --- | --- | --- |
| Kortix | One Docker Compose stack via `kortix self-host`. | An isolated sandbox per session, on its own branch. | The git repo: agents, skills, memory and connectors. |
| AgenticSeek | Clone, Docker and Python 3.10 on one machine. | The machine that runs the model. | The agent, its config and all local data. |
| OpenHands | Install on a laptop, a server or a VM. | The host, or an agent backend you point it at. | The console, the agent servers and your automations. |
| Open WebUI | Docker or Kubernetes; SQLite or PostgreSQL. | A companion terminal tool; isolated per person on Enterprise. | The interface, your models and your retrieval data. |

## How to decide

Self-hosting is the right move when the data, the model keys or the configuration must stay on infrastructure you control, and Kortix makes it free to start: one stack on a server you own, the same files on a laptop and on the server, and a review gate before work lands. Keep AgenticSeek when the team is one person and the whole point is that nothing leaves the machine. The rest comes down to whether your unit of work is a machine or a team.

For the head-to-head version of this decision, see [Kortix vs AgenticSeek](kortix-vs-agenticseek.md). For the full field, see [AgenticSeek alternatives, mapped](agenticseek-alternatives.md).
