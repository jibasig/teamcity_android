# Teamcity Android
Full docker compose setup for teamcity with teamcity agent.

Just edit the Dockerfile under android_agent to mount teamcity volumes to your host then run
```bash
docker-compose up -d
```
Teamcity will be running on port 8111
