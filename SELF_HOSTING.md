# OpenAgents Self-Hosting

This repository is the Xianniu AI Office fork of OpenAgents.

## Repository

Origin:

    https://github.com/ZyMousai/openagents.git

Upstream:

    https://github.com/openagents-org/openagents.git

Current branch:

    develop

## Local Path

    ~/openagents

## Workspace

Workspace name:

    Xianniu AI Office

Frontend:

    http://192.168.50.254:3000

Backend:

    http://192.168.50.254:8100

## Local Customizations

Important local files:

    workspace/backend/backend.Dockerfile
    workspace/docker-compose.override.yml

Current changes include:

- Aliyun PyPI mirror for backend Docker builds
- frontend exposed on port 3000
- backend exposed on port 8100
- frontend API URL configured for LAN access
- backend CORS configured for LAN frontend access

## Start

    cd ~/openagents/workspace
    sudo docker compose up -d

## Stop

    cd ~/openagents/workspace
    sudo docker compose down

## Status

    cd ~/openagents/workspace
    sudo docker compose ps

## Logs

Backend:

    sudo docker compose logs -f backend

Frontend:

    sudo docker compose logs -f frontend

## Database Migration

If the backend reports missing tables or schema errors:

    cd ~/openagents/workspace
    sudo docker compose exec backend alembic upgrade head

## OpenAgents Node

The Ubuntu server is paired as an OpenAgents Node.

Check daemon:

    agn status

Check runtimes:

    agn runtimes

Check autostart:

    agn autostart

The OpenAgents daemon uses a systemd user service.

Verify linger:

    loginctl show-user ubuntu -p Linger

Expected:

    Linger=yes

## AgentOS Integration

The AgentOS runtime is not maintained directly inside this repository.

See:

    zymousai/agentos-openagents-integration

That repository contains:

- A2A Gateway
- AgentOS OpenAgents runtime
- runtime install script
- recovery documentation

Current path:

    ~/agentos-openagents-integration

## Current Agent

    platform-builder

Current end-to-end path:

    OpenAgents Workspace
    -> OpenAgents Node
    -> AgentOS Runtime
    -> A2A Gateway
    -> AgentOS
    -> Ollama

## Updating From Upstream

Fetch official updates:

    git fetch upstream

Review changes before rebasing:

    git log --oneline --decorate --graph --max-count=20 --all

Rebase when appropriate:

    git rebase upstream/develop

Then push:

    git push origin develop

Do not blindly force push.

## Security

Never commit:

- workspace tokens
- pairing codes
- passwords
- API keys
- .env files
- private keys

Workspace tokens should be treated like passwords.

## Related Repositories

AgentOS platform:

    zymousai/agent-platform

AgentOS/OpenAgents integration:

    zymousai/agentos-openagents-integration
