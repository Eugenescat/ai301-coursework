### Issue ### 
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/26

Add a safety event count to the health check endpoint #26

The /health endpoint in api/routes/health.py reports safety_events_last_hour as the literal 0 and never reads the safety layer, so the field doesn't reflect any recorded event. SafetyMonitor.get_event_count() in safety/monitoring.py can supply per-type counts to fill it.

Relevant files:

api/routes/health.py
safety/monitoring.py
Estimated effort: 2–4 hours

### Claim ###

Hi, I'd like to work on this as my first contribution. I'll reproduce the hard-coded safety_events_last_hour: 0 in /health on current main, then post a repro report here before looking at how SafetyMonitor.get_event_count() could fill it.

### Reproduction Report ###

Reproduction environment:
commit f89c06f
ProductName:            macOS
ProductVersion:         26.5
BuildVersion:           25F71
arm64
Python 3.11.17
Docker version 24.0.6, build ed223bc
Docker Compose version v2.22.0-desktop.2
PostgreSQL：postgres:16-alpine
Redis：redis:7-alpine
ChromaDB：chromadb/chroma:0.4.22
Node: v23.11.0
npm: 10.9.2
SQLAlchemy 2.1.4

Reproduction steps:
1. start service
```
docker compose up -d
make setup
make run
```

2. call endpoint /health
``` 
curl -s http://localhost:8000/health
```

3. We shall see the result
```
 {"detail":{"status":"unhealthy","dependencies":{"postgres":"unhealthy","redis":"unhealthy","vector_db":"healthy"},"safety_events_last_hour":0,"timestamp":"2026-10-08T05:38:45.979450"}}
```

4. check status of db and redis
```
docker compose ps
```
```
NAME                               IMAGE                COMMAND                SERVICE   CREATED       STATUS                 PORTS
pathreview-ai301-fa26-s1-db-1      postgres:16-alpine   "docker-entrypoint.shpostgres"       db        2 hours ago   Up 2 hours (healthy)   0.0.0.0:5433->5432/tcp
pathreview-ai301-fa26-s1-redis-1   redis:7-alpine       "docker-entrypoint.shredis-server"   redis     2 hours ago   Up 2 hours (healthy)   0.0.0.0:6379->6379/tcp
```
we can see both postgres and redis are in status healthy. So the unhealthy statuses come from other code bugs.

   
5. manually add one safety event in redis, to test if "safety_events_last_hour" will updated accordingly
```
docker compose exec redis redis-cli DEL safety:events:pii_detected
docker compose exec redis redis-cli INCR safety:events:pii_detected
```

we shall see at the terminal:
```
(integer) 0
(integer) 1
```

6. again call endpoint /health
``` 
curl -s http://localhost:8000/health
```
```
{"detail":{"status":"unhealthy","dependencies":{"postgres":"unhealthy","redis":"unhealthy","vector_db":"healthy"},"safety_events_last_hour":0,"timestamp":"2026-10-08T06:40:15.052858"}}
```
Redis holds 1, but /health still returns 0, because api/routes/health.py:80 assigns the literal 0 and never calls SafetyMonitor.

### Next step ###
Next I'll look at how SafetyMonitor.get_event_count() could fill this field.