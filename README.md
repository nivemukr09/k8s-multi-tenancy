## Kubernetes Multi-Tenancy Setup
This project demonstrates a basic multi-tenancy setup in Kubernetes, where different teams (like team-alpha and team-beta) are isolated using Namespaces, Network Policies, and RBAC (Role-Based Access Control).
## Project Structure
.
├── team-alpha-deployment.yaml
├── team-alpha-networkpolicy.yaml
├── team-alpha-role.yaml
├── team-alpha-rolebinding.yaml
├── team-beta-deployment.yaml
├── team-beta-networkpolicy.yaml
├── team-beta-role.yaml
├── team-beta-rolebinding.yaml
Each team has:

A Deployment (basic app pod)

A NetworkPolicy (restricts network access)

A Role (defines allowed Kubernetes actions)

A RoleBinding (binds users to roles)

## Steps to Deploy
1. Create Namespaces
```bash
kubectl create namespace team-alpha
kubectl create namespace team-beta
```

3. Apply Manifests
For Team Alpha:
```bash
kubectl apply -f team-alpha-deployment.yaml
kubectl apply -f team-alpha-networkpolicy.yaml
kubectl apply -f team-alpha-role.yaml
kubectl apply -f team-alpha-rolebinding.yaml
```

For Team Beta:
```bash
kubectl apply -f team-beta-deployment.yaml
kubectl apply -f team-beta-networkpolicy.yaml
kubectl apply -f team-beta-role.yaml
kubectl apply -f team-beta-rolebinding.yaml
```

3. Verify
Check if everything is deployed:
```bash
kubectl get all -n team-alpha
kubectl get all -n team-beta
```
### What This Achieves
✅ Isolation of team resources using Namespaces
✅ Controlled network traffic between pods
✅ Role-based access control over Kubernetes objects

### Notes
-> You can extend this setup by adding ResourceQuotas, LimitRanges, and more strict NetworkPolicies based on your need.

-> This setup is mainly for learning purposes. In production, you would combine it with authentication systems (like OIDC, SSO).
