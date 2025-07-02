
cat > ADR-0001-multicloud.md << 'EOF'
# ADR-0001-multicloud.md (GCP + Snowflake) 

## status
Proposed 
## Context
- Need streaming ingestion and DW thats escapes quickly
- Offshore clients and corp (finance) required latency < 60 s and governance

## Decision
**GCP** (Pub/Sub, BigQuery, Storage) for ingestion, processing and streaming, and ***Snowflake*** for Data Vault and enterprise analytics.  

## Consequences
**Positives**:

– Fast setup in Snowflake, low Ops in GCP.

– Native support for external tables in BigQuery.

**Negatives**:

– Slightly higher multicloud cost.

– Complexity of IAM on two platforms.

## Alternatives Considered
1. **Only GCP** (BigQuery + Dataflow):

– + Lower operational cost.

– – Data Vault in BigQuery requires more manual work.

2. **Only Snowflake** (Snowpipe + Streams):

– + Consistency in DWH.

– – Pure streaming is not as simple without GCP.
EOF
