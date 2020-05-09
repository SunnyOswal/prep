 Deployment creates a rollout with a revision (version). This keeps us track the deployments and for rollbacks.

# Deployment Strategy:
+ Recreate
  + Remove all old ones and then create new ones but this leads to application downtime.
+ Rolling Updates
  + This is default deployment strategy.
  + To avoid downtime of application , update is one by one by adding new one & then removing old one and continuing like that.
+ Rollback
  + k8s allow to revert to old version by running "rollout undo version" command with kubectl
  

+
