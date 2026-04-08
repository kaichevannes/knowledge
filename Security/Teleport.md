In Teleport because we just have the Proxy Service exposed to the internet and
use mTLS with reverse tunnels to each of the nodes in the cluster, there are no
exposed endpoints.

## Machine & Workload Identity
CI/CD pipelines, microservices, MCP servers often have high privilege standing
credentials. We usually have far more machine credentials than human.

### tbot
After joining the Teleport cluster with a join token, `tbot` runs in daemon mode
or oneshot mode. In daemon mode tbot will contiuously refresh its certificate.
In oneshot mode an external authority will provide a dynamic join token which
can be exchanged for a non-renewable certificate.

## Auditing
Centralised auditing of human and machine identity. Replay of sessions.
