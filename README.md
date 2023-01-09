It's program with workarounds for some nomad common issues:

_hashicorp/nomad#3093 Forcing a placement with failed deployment_. This forces placement of undone allocations of specified job (or all jobs with `finish-all-failed-deployment`) 

    nmd finish-failed-deployment <job-id>

_hashicorp/nomad#698 Add ability to restart all running tasks/allocs of a job_. This forces deployment of specified job (or only one group in job if group specified) 

    nmd redeploy <job-id> (<group>)

_hashicorp/nomad#10727 NOMAD_ALLOC_INDEX is not always unique within a single job version_. This resolves non uniq `NOMAD_ALLOC_INDEX` of specified job by temporarily changing number counts of affected groups (use `resolve-all-collisions` to apply fix for all jobs). 

    nmd resolve-collisions <job-id>

_Lots of issues about rebalancing (hashicorp/nomad#10039, hashicorp/nomad#1635, hashicorp/nomad#8368)_. This is a partial workaround that allows manually moving group(s) off the server.

    nmd move <job-id> 'group!=srv1,group!=srv2'

## Installation

Only ruby installation required. Copy `nmd` script somewhere in `PATH`, mare sure it has execute permission. Script requires a local `nomad` agent installed.

