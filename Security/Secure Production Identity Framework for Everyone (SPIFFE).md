SPIFFE uses SVIDs (SPIFFE Verifiable Identity Document) — usually an X.509
certificate or JWT — to cryptographically prove the identity (SPIFFE ID) of
workloads. Workloads request an identity from an agent (e.g. SPIRE Agent or
Teleport tbot) and after workload attestation are issued an SVID. Workload
attestation is basically inspecting metadata about the workload like binary
path, UID, container ID.
