# Autoscalar 


export KO_DOCKER_REPO='docker.io/arunjoykalathoor'

ko build ./cmd/autoscaler

ko apply -f config/core/deployments/autoscaler.yaml