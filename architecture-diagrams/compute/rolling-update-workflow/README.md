# Rolling Update Workflow

This diagram illustrates how Google Compute Engine Managed Instance Groups perform rolling updates using a new instance template.

Instead of replacing all virtual machines simultaneously, the Managed Instance Group updates instances incrementally, helping maintain application availability while deploying new configurations.

## Key Concepts

- Instance Templates define VM configurations.
- Managed Instance Groups coordinate VM lifecycle management.
- Rolling updates replace instances sequentially.
- Existing traffic continues to be served during deployment.
- Health checks verify new instances before continuing.

## Benefits

- Minimal downtime
- Consistent deployments
- High availability
- Simplified rollback strategies
- Automated infrastructure management

## ACE Exam Recognition

When you see:

- **Instance Template → Managed Instance Group → Rolling Action**

it indicates a **rolling update deployment strategy**, where VMs are replaced gradually to maintain service availability.
