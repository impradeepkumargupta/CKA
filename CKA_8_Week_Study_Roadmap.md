# 8-Week CKA Exam Preparation Roadmap
## Kubernetes administration, hands-on labs, and exam practice

**Study period:** Saturday, 17 October 2026 – Friday, 11 December 2026  
**Total time:** 8 weeks × 15 hours = **120 hours**  
**Schedule:** Monday–Friday 1 hour/day; Saturday and Sunday 5 hours/day  
**Primary goal:** Pass the Certified Kubernetes Administrator (CKA) performance-based exam.

This plan is intentionally **CKA-only**. It does not allocate study time to GKE-specific operations, Google Cloud IAM, Workload Identity Federation, or cloud-provider networking except where generic Kubernetes concepts overlap. The learner already has a Cloud/DevOps, Kubernetes, Terraform, and Linux foundation, so the plan prioritizes command-line fluency, exam-objective coverage, troubleshooting, and timed labs over introductory videos.

> **Version note:** The Linux Foundation CKA page currently identifies Kubernetes v1.35 as the exam version, but the exam environment can change. Re-check the official CKA page, curriculum, candidate handbook, and allowed-resources policy shortly before the exam.

---

## 1. Exam scope and priorities

The published CKA domain weights are:

| Domain | Weight | Planning priority |
|---|---:|---|
| Troubleshooting | 30% | Highest |
| Cluster Architecture, Installation & Configuration | 25% | Very high |
| Services & Networking | 20% | High |
| Workloads & Scheduling | 15% | High |
| Storage | 10% | Important |

These weights are the published domain weights, not a prediction of the exact tasks on any individual exam. Follow the current official curriculum if it changes.

### Competencies to cover

#### Cluster Architecture, Installation & Configuration — 25%
- Role-Based Access Control (RBAC): Roles, ClusterRoles, RoleBindings, ClusterRoleBindings, ServiceAccounts, `kubectl auth can-i`.
- Cluster setup and lifecycle using `kubeadm`: initialization, joining nodes, version upgrades, cluster health.
- Control-plane and worker-node components; kubelet, container runtime, API server, scheduler, controller manager, etcd.
- Highly available control-plane concepts and cluster lifecycle.
- etcd snapshot and restore concepts and practical recovery in a disposable kubeadm environment.
- Helm and Kustomize for installing/configuring cluster components.
- Extension interfaces: CNI, CSI, CRI.
- CustomResourceDefinitions (CRDs), operators, and how to inspect and use custom resources.

#### Workloads & Scheduling — 15%
- Pods, Deployments, ReplicaSets, rolling updates, rollbacks, scaling.
- ConfigMaps and Secrets.
- Jobs and CronJobs.
- Requests, limits, QoS, OOMKilled and resource monitoring.
- Readiness, liveness and startup probes.
- Node selectors, node affinity/anti-affinity, taints/tolerations, topology spread, cordon/drain.
- Pod disruption budgets and robust, self-healing deployments.
- Workload autoscaling and the requirements for metrics-based scaling.
- Admission and scheduling concepts in the current curriculum.

#### Services & Networking — 20%
- Pod-to-Pod connectivity and cluster network fundamentals.
- ClusterIP, NodePort, LoadBalancer, selectors, ports and EndpointSlices/endpoints.
- CoreDNS, Service discovery, namespaces and DNS troubleshooting.
- NetworkPolicy ingress/egress and selector logic.
- Ingress resources and controllers; Gateway API concepts as specified in the current curriculum.
- Troubleshooting Services, DNS, routes, ports, policies and application listeners.

#### Storage — 10%
- Volumes, PersistentVolumes (PV), PersistentVolumeClaims (PVC), StorageClasses.
- Dynamic provisioning, access modes, reclaim policies and binding.
- Volume mounts, read/write behavior, permissions and storage-related events.
- Diagnosing Pending PVCs, failed mounts and persistence issues.

#### Troubleshooting — 30%
- Cluster and node health; node conditions, kubelet and container runtime.
- Cluster component and control-plane troubleshooting.
- CPU/memory monitoring, resource pressure and container output streams.
- Pod failures, probes, image pull failures, crash loops and rollout failures.
- Service connectivity, DNS, endpoints, NetworkPolicy and port errors.
- Evidence-first diagnosis: events, logs, status, configuration, metrics and verification.

---

## 2. Resource library

Use official documentation as the reference source. Videos can introduce a topic, but every study block should end with a command-line task.

### Official CKA and exam resources
1. **CKA certification page, domains, exam details and links to the handbook/curriculum:**  
   https://www.cncf.io/training/certification/cka/
2. **Linux Foundation CKA page and exam simulator information:**  
   https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/
3. **Linux Foundation certification FAQ and allowed resources:**  
   https://training.linuxfoundation.org/about/faqs/certification-faq/
4. **Official Kubernetes documentation:**  
   https://kubernetes.io/docs/home/
5. **kubectl reference:**  
   https://kubernetes.io/docs/reference/kubectl/
6. **Kubernetes task tutorials:**  
   https://kubernetes.io/docs/tasks/
7. **Kubernetes concepts:**  
   https://kubernetes.io/docs/concepts/

### Official topic links
- Architecture: https://kubernetes.io/docs/concepts/architecture/
- Pods: https://kubernetes.io/docs/concepts/workloads/pods/
- Deployments: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
- Jobs and CronJobs: https://kubernetes.io/docs/concepts/workloads/controllers/job/
- ConfigMaps: https://kubernetes.io/docs/concepts/configuration/configmap/
- Secrets: https://kubernetes.io/docs/concepts/configuration/secret/
- Resource management: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
- Probes: https://kubernetes.io/docs/concepts/configuration/liveness-readiness-startup-probes/
- Scheduling and eviction: https://kubernetes.io/docs/concepts/scheduling-eviction/
- Services: https://kubernetes.io/docs/concepts/services-networking/service/
- DNS for Services and Pods: https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/
- NetworkPolicy: https://kubernetes.io/docs/concepts/services-networking/network-policies/
- Ingress: https://kubernetes.io/docs/concepts/services-networking/ingress/
- Gateway API task: https://kubernetes.io/docs/concepts/services-networking/gateway/
- Storage: https://kubernetes.io/docs/concepts/storage/
- Persistent volumes: https://kubernetes.io/docs/concepts/storage/persistent-volumes/
- StorageClasses: https://kubernetes.io/docs/concepts/storage/storage-classes/
- RBAC: https://kubernetes.io/docs/reference/access-authn-authz/rbac/
- ServiceAccounts: https://kubernetes.io/docs/concepts/security/service-accounts/
- kubeadm: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/
- Certificates: https://kubernetes.io/docs/setup/best-practices/certificates/
- etcd documentation: https://etcd.io/docs/
- Helm documentation: https://helm.sh/docs/
- Kustomize documentation: https://kubectl.docs.kubernetes.io/guides/introduction/kustomize/
- CRDs: https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/
- Operators: https://kubernetes.io/docs/concepts/extend-kubernetes/operator/

### Hands-on environments and practice
- **kind quick start:** https://kind.sigs.k8s.io/docs/user/quick-start/
- **Minikube start:** https://minikube.sigs.k8s.io/docs/start/
- **Killercoda Kubernetes labs:** https://killercoda.com/kubernetes
- **Killer Shell:** https://killer.sh/ (check the simulator included with the exam purchase)
- **Linux Foundation exam simulator:** check current inclusion and activation terms on the official CKA page.

Use one local environment consistently for most tasks. A multi-node `kind` or kubeadm-based lab is useful for node and cluster administration exercises; some control-plane and etcd tasks require a kubeadm environment rather than a single-node application lab. Do not spend time rebuilding environments every week.

---

## 3. Lab setup and operating rules

### Before Week 1
- [ ] Choose a local Kubernetes environment: `kind`, Minikube, or a disposable kubeadm lab.
- [ ] Confirm `kubectl` is installed and compatible with the cluster.
- [ ] Create a dedicated folder for manifests and notes, for example `cka-8-weeks/`.
- [ ] Keep one folder per week and one file named `mistake-log.md`.
- [ ] Practise context and namespace checks before every change.
- [ ] Make sure you can edit YAML quickly using your preferred terminal editor.
- [ ] Avoid using production/shared clusters for failure injection.

### Useful shell and kubectl patterns
```bash
# Context safety
kubectl config get-contexts
kubectl config current-context
kubectl config use-context <context>
kubectl get namespaces

# Fast inspection
kubectl get pods -A -o wide
kubectl get deploy,rs,svc -A
kubectl describe pod <pod> -n <namespace>
kubectl get events -A --sort-by=.metadata.creationTimestamp
kubectl logs <pod> -n <namespace>
kubectl logs <pod> -n <namespace> --previous

# Generate starter YAML, then edit and apply
kubectl create deployment web --image=nginx --dry-run=client -o yaml
kubectl run test-pod --image=busybox:1.36 --restart=Never --dry-run=client -o yaml
kubectl explain pod.spec
kubectl apply -f <file.yaml>
kubectl diff -f <file.yaml>

# Workload operations
kubectl rollout status deployment/<name>
kubectl rollout history deployment/<name>
kubectl rollout undo deployment/<name>
kubectl scale deployment/<name> --replicas=3

# Scheduling and resource evidence
kubectl get nodes
kubectl describe node <node>
kubectl top nodes
kubectl top pods -A

# RBAC
kubectl auth can-i get pods -n <namespace>
kubectl auth can-i create deployments --as=system:serviceaccount:<namespace>:<serviceaccount> -n <namespace>
```

`kubectl top` requires a functioning metrics pipeline. Use the command as a diagnostic tool, and know how to distinguish a missing metrics source from genuinely low resource usage.

### The daily 60-minute method
For Monday–Friday:
- **10 min:** recall commands and key concepts without notes.
- **25 min:** build a manifest or complete a targeted lab.
- **15 min:** troubleshoot and verify.
- **10 min:** write the root cause, fix and lesson in the mistake log.

### The weekend 5-hour method
Use five focused blocks, with short breaks:
1. 60 min: revise the week's concepts.
2. 90 min: guided build lab.
3. 60 min: failure-injection lab.
4. 60 min: timed exam-style tasks.
5. 30 min: review mistakes and update notes.

The exact split can vary, but keep the total at five hours per day.

---

# 4. The 8-week day-by-day roadmap

## Week 1 — CLI fluency, Kubernetes objects and workload lifecycle
**Dates:** Saturday, 17 October – Friday, 23 October 2026  
**Hours:** 15  
**Goal:** Work confidently from the command line; create and troubleshoot common workload objects.

### Topics and subtopics
- Kubernetes architecture: API server, etcd, scheduler, controller manager, kubelet, container runtime, kube-proxy.
- Desired state, reconciliation, API objects and `metadata/spec/status`.
- Namespaces, labels, selectors, annotations and imperative commands.
- Pods, Deployments, ReplicaSets and rollout lifecycle.
- YAML structure, `kubectl explain`, generated manifests and `--dry-run=client`.
- Container commands/arguments, environment variables, ConfigMaps and Secrets.
- `get`, `describe`, `logs`, `exec`, `events`, JSONPath and output formatting.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 17 Oct | 5h | Architecture; API objects; namespaces; context safety; basic `kubectl` operations. | Set up lab. Sketch control-plane/worker components. Create namespaces and inspect nodes, Pods and events. Write a 20-command cheat sheet. |
| Sun 18 Oct | 5h | YAML; Pods; Deployments; ReplicaSets; selectors; scaling; rollout status/history/undo. | Create a 3-replica Deployment, update its image, inspect the ReplicaSet, roll back and verify available replicas. |
| Mon 19 Oct | 1h | `kubectl get`, `describe`, `explain`, `logs`, `exec`, events and namespaces. | Diagnose a deliberately misconfigured Pod from evidence. |
| Tue 20 Oct | 1h | YAML fields, imperative generation, `--dry-run=client -o yaml`, `apply` and `diff`. | Generate and edit two manifests without copying a complete example. |
| Wed 21 Oct | 1h | Labels, selectors, annotations, ConfigMaps and Secrets. | Repair a Deployment/Service selector mismatch and inject configuration. |
| Thu 22 Oct | 1h | Container commands, arguments, environment, restart policy and probes. | Fix a startup or readiness probe failure. |
| Fri 23 Oct | 1h | Review, memory-based commands and short timed tasks. | Complete 8 tasks; update the mistake log. |

### Weekend lab: break and repair a web application
Create a Deployment and expose it through a Service. Introduce one fault at a time:
1. Invalid image tag → `ImagePullBackOff`.
2. Invalid startup command → repeated container exits.
3. Incorrect label selector → no matching endpoints.
4. Incorrect readiness probe → Pod is running but not ready.
5. Bad container port or Service `targetPort` → connection failure.

For each issue, capture:
- Symptom.
- Diagnostic command and evidence.
- Root cause.
- Minimal fix.
- Verification.

### Week 1 completion gate
- [ ] Create and edit YAML from memory.
- [ ] Scale, update and roll back a Deployment.
- [ ] Explain Pod phase vs. container state vs. readiness.
- [ ] Diagnose `ImagePullBackOff` and `CrashLoopBackOff`.
- [ ] Find and fix a label/selector mismatch.

---

## Week 2 — Workloads, configuration, resources and scheduling
**Dates:** Saturday, 24 October – Friday, 30 October 2026  
**Hours:** 15  
**Goal:** Solve workload and scheduling tasks quickly, including resource-related failures.

### Topics and subtopics
- Deployments, rollout strategies, `maxSurge`, `maxUnavailable`, history and rollback.
- ConfigMaps and Secrets as environment variables and mounted files.
- Readiness, liveness and startup probes.
- CPU/memory requests and limits; QoS classes; OOMKilled; CPU throttling.
- Jobs, CronJobs, init containers and sidecars.
- Node selectors, node affinity/anti-affinity, taints and tolerations.
- Topology spread constraints, cordon/drain, evictions and PodDisruptionBudgets.
- HPA, metrics requirements and basic workload autoscaling.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 24 Oct | 5h | Resource requests/limits, QoS, OOMKilled, throttling, probes, rollout strategies. | Deploy workloads with intentionally poor resource settings; diagnose and fix them. Practise rollout update and rollback. |
| Sun 25 Oct | 5h | Node selectors, affinity, taints/tolerations, topology spread, cordon/drain, PDBs, Jobs/CronJobs and HPA. | Make a Pod unschedulable, diagnose the event, repair scheduling, run a Job and a CronJob. |
| Mon 26 Oct | 1h | Deployment update strategy and rollout history. | Roll out a bad image and undo it safely. |
| Tue 27 Oct | 1h | ConfigMaps/Secrets update behavior and mounted configuration. | Change configuration and explain whether a restart is required. |
| Wed 28 Oct | 1h | CPU/memory requests, limits, QoS and metrics. | Diagnose an OOMKilled container; inspect resource requests and limits. |
| Thu 29 Oct | 1h | Jobs, CronJobs, init containers, sidecars and failure status. | Create a Job and a scheduled task; diagnose a failed run. |
| Fri 30 Oct | 1h | Scheduling revision and timed challenge. | Complete 5 scheduling/resource tasks in 45 minutes. |

### Required labs
- Create a Deployment with 3 replicas and perform a rolling update.
- Roll back an unsuccessful release.
- Configure a ConfigMap and Secret and consume them in a Pod.
- Configure readiness, liveness and startup probes correctly.
- Reproduce an OOMKilled container and explain the likely cause.
- Schedule a Pod using a node selector or affinity.
- Demonstrate a taint/toleration interaction.
- Cordon and drain a disposable node; understand PDB and DaemonSet effects.
- Create an HPA and explain why it requires metrics.
- Create a Job and CronJob.

### Week 2 completion gate
- [ ] Diagnose why a Pod is Pending.
- [ ] Distinguish scheduling failure from startup/readiness failure.
- [ ] Explain requests vs. limits and OOMKilled.
- [ ] Use affinity and taints/tolerations.
- [ ] Perform rollout and rollback without a tutorial.

---

## Week 3 — Services, DNS, NetworkPolicy and ingress routing
**Dates:** Saturday, 31 October – Friday, 6 November 2026  
**Hours:** 15  
**Goal:** Troubleshoot traffic from one Pod to another through Kubernetes Services and ingress routing.

### Topics and subtopics
- Pod networking model and Pod-to-Pod connectivity.
- Service types: ClusterIP, NodePort and LoadBalancer.
- Service selectors, `port`, `targetPort`, named ports and EndpointSlices.
- CoreDNS, service discovery, namespace search paths and FQDNs.
- NetworkPolicy ingress/egress, selectors, default-deny and allowed traffic.
- Ingress resources/controllers and Gateway API concepts.
- TCP ports, listeners, DNS, application health and connectivity checks.
- Basic `curl`, `wget`, `dig`, `nslookup`, `ss` and `ip` usage.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 31 Oct | 5h | Pod network model; Service types; selectors; ports; endpoints. | Deploy frontend/backend. Expose backend with ClusterIP and test from another Pod. |
| Sun 1 Nov | 5h | DNS; CoreDNS; NetworkPolicy; Ingress and Gateway concepts; troubleshooting tools. | Break and repair 4 traffic paths. Inspect Service and EndpointSlices and apply a restrictive NetworkPolicy. |
| Mon 2 Nov | 1h | Service selectors, ports and EndpointSlices. | Repair a Service with no ready endpoints. |
| Tue 3 Nov | 1h | DNS names, namespaces, search paths and FQDNs. | Resolve a Service from another namespace and troubleshoot a bad name. |
| Wed 4 Nov | 1h | NetworkPolicy ingress/egress and selector logic. | Permit frontend-to-backend traffic while blocking an unrelated client. |
| Thu 5 Nov | 1h | Ingress/controller relationship, routing rules, TLS concepts and Gateway API overview. | Read an Ingress/Gateway manifest and explain how traffic is routed. |
| Fri 6 Nov | 1h | Timed networking revision. | Fix a selector mismatch, wrong target port and DNS/network-policy failure. |

### Failure-injection checklist
1. Wrong Service selector.
2. Wrong `targetPort`.
3. Backend process listens on the wrong port.
4. Incorrect DNS name or namespace.
5. Restrictive NetworkPolicy.
6. Application Pod is unready and absent from usable endpoints.
7. Ingress references the wrong Service or port.
8. A DNS query fails: determine whether the name, Service, Pod or DNS component is at fault.

Do not assume every local cluster supports the same ingress controller, Gateway implementation or NetworkPolicy enforcement. Install the required implementation in a disposable lab if needed, or use a simulator that provides it.

### Week 3 completion gate
- [ ] Explain Service `port` vs. `targetPort`.
- [ ] Trace a request through Service, EndpointSlice and Pod.
- [ ] Resolve Services by DNS name across namespaces.
- [ ] Diagnose NetworkPolicy selector/rule errors.
- [ ] Explain the difference between an Ingress resource and its controller.

---

## Week 4 — Storage, RBAC and security-related administration
**Dates:** Saturday, 7 November – Friday, 13 November 2026  
**Hours:** 15  
**Goal:** Complete the Storage domain and build confidence with RBAC tasks.

### Topics and subtopics
- Volumes, PVs, PVCs and StorageClasses.
- Dynamic provisioning, access modes, reclaim policies and binding.
- Volume mounts, read-only mounts, filesystem permissions and persistence.
- CSI concepts and storage-related events.
- Kubernetes identity: users, groups, ServiceAccounts and API authentication.
- RBAC Roles, ClusterRoles, RoleBindings and ClusterRoleBindings.
- Namespace scope vs. cluster scope.
- `kubectl auth can-i`, impersonation for testing and least privilege.
- Secrets, security contexts and Linux ownership/permissions as supporting knowledge.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 7 Nov | 5h | PV/PVC/StorageClass; dynamic provisioning; access modes; reclaim policies; mounts. | Provision storage, write data, recreate a Pod and confirm persistence. Diagnose a Pending PVC. |
| Sun 8 Nov | 5h | RBAC objects; ServiceAccounts; namespace vs. cluster permissions; auth checks; volume permissions. | Create a read-only Role and binding. Test allowed and denied actions. Troubleshoot a mount permission issue. |
| Mon 9 Nov | 1h | PVC lifecycle and binding. | Diagnose a PVC that remains Pending using events and StorageClass details. |
| Tue 10 Nov | 1h | Access modes, reclaim policies, volume mount paths and permissions. | Fix a wrong mount path or read-only/write-permission issue. |
| Wed 11 Nov | 1h | Roles, ClusterRoles, RoleBindings and ClusterRoleBindings. | Grant only `get`, `list`, and `watch` on Pods in one namespace. |
| Thu 12 Nov | 1h | ServiceAccounts and `kubectl auth can-i`. | Verify allowed and denied actions for a test identity. |
| Fri 13 Nov | 1h | Storage/RBAC timed revision. | Complete 5 tasks in 45 minutes. |

### Week 4 completion gate
- [ ] Explain why a PVC is Pending.
- [ ] Distinguish a PVC binding problem from a container mount/permission problem.
- [ ] Create a Role and RoleBinding with least privilege.
- [ ] Verify access using `kubectl auth can-i`.
- [ ] Explain the scope difference between RoleBinding and ClusterRoleBinding.

---

## Week 5 — Cluster administration, kubeadm, control plane and etcd
**Dates:** Saturday, 14 November – Friday, 20 November 2026  
**Hours:** 15  
**Goal:** Cover cluster administration and lifecycle competencies in the current CKA curriculum.

### Topics and subtopics
- kubeadm initialization and node join workflow.
- API server, etcd, scheduler, controller manager, kubelet and container runtime.
- Static Pods and control-plane component manifests.
- Cluster health, kubelet logs, node conditions and container runtime failures.
- kubeconfig structure, contexts and safe context switching.
- Cluster version lifecycle and kubeadm upgrade workflow.
- etcd snapshots, backup verification and restore concepts.
- Certificates and API connectivity failures.
- High-availability control-plane concepts.
- CNI/CSI/CRI roles and common symptoms of a broken integration.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 14 Nov | 5h | kubeadm architecture; bootstrap; static Pods; control-plane components; kubelet and runtime. | Use a kubeadm-based lab or guided simulator. Identify component configuration and inspect cluster health. |
| Sun 15 Nov | 5h | etcd snapshot/restore concepts; cluster upgrade workflow; certificates; HA concepts; node failure diagnosis. | Complete a guided backup/recovery or upgrade lab in a disposable environment. Document exact verification steps. |
| Mon 16 Nov | 1h | kubeconfig clusters, users, contexts and namespaces. | Switch between contexts safely and verify the target before making changes. |
| Tue 17 Nov | 1h | kubeadm init/join/upgrade concepts and component roles. | Explain the workflow and practise the commands in a safe simulator/lab. |
| Wed 18 Nov | 1h | Node NotReady, kubelet, runtime, node conditions and events. | Diagnose a simulated node-health issue. |
| Thu 19 Nov | 1h | etcd snapshot/restore and certificate/API access failure concepts. | Practise the relevant workflow in a guided lab; document prechecks and validation. |
| Fri 20 Nov | 1h | Cluster administration revision. | Complete 5 administration tasks or scenario questions under a 45-minute limit. |

### Cluster failure scenarios
- Wrong kubeconfig context.
- Worker node becomes NotReady.
- Kubelet fails or cannot communicate with the API server.
- Static Pod manifest has an invalid setting.
- API server is unavailable or rejects connections.
- Certificate expiry or trust issue causes API access failure.
- etcd backup is missing, invalid or has not been tested.
- Cluster upgrade is blocked by version constraints or node health.
- CNI/CSI/CRI issue causes workload or node symptoms.

**Important:** Use a disposable kubeadm environment or a simulator for control-plane, certificate and etcd exercises. Do not attempt destructive recovery commands on a shared cluster. The CKA may test practical cluster-administration knowledge, so do not substitute GKE-managed control-plane operations for kubeadm practice.

### Week 5 completion gate
- [ ] Explain each control-plane and node component.
- [ ] Inspect kubeconfig and safely switch contexts.
- [ ] Understand kubeadm initialization, join and upgrade flow.
- [ ] Explain etcd backup/restore and verify a guided lab.
- [ ] Diagnose a NotReady node using evidence.

---

## Week 6 — Troubleshooting mastery, Helm, Kustomize, CRDs and operators
**Dates:** Saturday, 21 November – Friday, 27 November 2026  
**Hours:** 15  
**Goal:** Build a repeatable troubleshooting method and cover the additional competencies in the current curriculum.

### Topics and subtopics
- Evidence-first diagnosis: status → events → logs → configuration → dependencies → fix → verification.
- Cluster and node troubleshooting.
- Pod lifecycle, probes, image pulls, scheduling, resources and rollout issues.
- Service, DNS, endpoints and NetworkPolicy failures.
- Helm: repositories, charts, release install/upgrade/rollback/status.
- Kustomize: bases, overlays, patches and generated configuration.
- CRDs and custom resources; discover APIs using `kubectl api-resources` and `kubectl explain`.
- Operators: controller/reconciliation model and inspecting operator-created resources.
- Mixed troubleshooting and time-boxed task selection.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 21 Nov | 5h | Troubleshooting Pods, nodes, control plane, resources, logs, events, Services and DNS. | Run a 6-fault gauntlet. Diagnose before fixing; verify every repair. |
| Sun 22 Nov | 5h | Helm install/upgrade/rollback; Kustomize base/overlay; CRDs, custom resources and operator model. | Install or inspect a chart, customize a manifest with Kustomize, and inspect a CRD/custom resource in a suitable lab. |
| Mon 23 Nov | 1h | Structured troubleshooting and evidence collection. | Diagnose one failure using a written hypothesis/evidence/fix/verification sequence. |
| Tue 24 Nov | 1h | Helm basics: chart, release, values, status and rollback. | Inspect a release and perform a safe install/upgrade/rollback if a chart is available. |
| Wed 25 Nov | 1h | Kustomize: base, overlay, patch and generated resources. | Build and apply a small overlay without duplicating the base manifest. |
| Thu 26 Nov | 1h | CRDs, custom resources, API discovery and operators. | Inspect `api-resources`, a CRD and a custom resource in a prepared lab. |
| Fri 27 Nov | 1h | Mixed troubleshooting drill. | Complete 5 mixed tasks in 45 minutes and update the weakness list. |

### Troubleshooting protocol
For every incident, follow the same order:

1. **Confirm target:** context, namespace, object name and scope.
2. **Observe:** `get`, `describe`, events, status and conditions.
3. **Inspect output:** container logs, previous logs, process/listener behavior and relevant configuration.
4. **Check dependencies:** selectors, endpoints, DNS, PVCs, permissions, scheduling constraints and resource availability.
5. **Form a hypothesis:** explain what evidence supports it.
6. **Make the smallest safe change.**
7. **Verify:** desired state, readiness, endpoints, successful request, or recovered node.
8. **Record:** root cause, fix and prevention.

### Week 6 completion gate
- [ ] Complete six troubleshooting cases with evidence and verification.
- [ ] Perform basic Helm release operations.
- [ ] Build a Kustomize overlay.
- [ ] Discover and inspect a CRD/custom resource in a prepared environment.
- [ ] Explain how an operator reconciles custom-resource state.

---

## Week 7 — Timed mocks and focused remediation
**Dates:** Saturday, 28 November – Friday, 4 December 2026  
**Hours:** 15  
**Goal:** Move from topic learning to exam execution. Practise all domains and analyse every error.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 28 Nov | 5h | Timed mock block 1 (2h); review (1h); redo failed workload, storage and networking tasks (2h). | Complete the mock within time. Record score, time per task and root cause for each error. |
| Sun 29 Nov | 5h | Timed mock block 2 (2h); review (1h); redo cluster/RBAC/troubleshooting tasks (2h). | Complete a second distinct timed practice attempt and create a ranked weakness list. |
| Mon 30 Nov | 1h | Weakest domain #1. | Complete 3 related tasks without notes. |
| Tue 1 Dec | 1h | Services, DNS and NetworkPolicy. | Repair a broken service path under a time limit. |
| Wed 2 Dec | 1h | Storage, RBAC and scheduling. | Complete 3 short tasks and verify permissions/binding/scheduling. |
| Thu 3 Dec | 1h | Cluster administration and component troubleshooting. | Diagnose a node/control-plane/access scenario. |
| Fri 4 Dec | 1h | Error-log review and command fluency. | Produce a five-item weakness list with verified fixes. |

### Mock review rubric
For every task, record:

| Field | What to capture |
|---|---|
| Result | Correct, partial or incorrect |
| Time spent | Actual minutes |
| Error category | Knowledge, syntax, context, diagnosis, verification or time management |
| Root cause | Why the first attempt failed |
| Better approach | Shortest reliable command sequence |
| Retest | Date/time you solved it again without notes |

Do not repeat a mock immediately just to obtain a higher score. Retest the specific weak task types in a fresh state.

### Week 7 completion gate
- [ ] Two substantial timed practice attempts completed.
- [ ] Every failed task reviewed and classified.
- [ ] Top five weak task types ranked.
- [ ] At least one previously failed task from each weak domain solved again without notes.

---

## Week 8 — Final mocks, weak areas and exam readiness
**Dates:** Saturday, 5 December – Friday, 11 December 2026  
**Hours:** 15  
**Goal:** Demonstrate repeatable performance and eliminate recurring mistakes. Avoid starting unrelated new material.

### Day-by-day plan

| Date | Time | Study and subtopics | Lab / deliverable |
|---|---:|---|---|
| Sat 5 Dec | 5h | Full timed mock (2h); review (1h); redo the hardest tasks (2h). | Complete a full mock and verify every corrected task. |
| Sun 6 Dec | 5h | Troubleshooting gauntlet (2h); second timed mixed set (1h); review/redo (2h). | Diagnose at least 8 different faults; record evidence, root cause, fix and verification. |
| Mon 7 Dec | 1h | Weakest domain #1 from mock results. | Complete 3 timed tasks without notes. |
| Tue 8 Dec | 1h | Weakest domain #2 from mock results. | Complete 3 timed tasks without notes. |
| Wed 9 Dec | 1h | Mixed CLI, YAML, RBAC, storage and Service tasks. | Complete 5 short tasks in 45 minutes and use the remaining time to verify. |
| Thu 10 Dec | 1h | Exam logistics, allowed resources, context safety, final command recall. | Review the current candidate handbook and allowed-resources policy. |
| Fri 11 Dec | 1h | Light revision only; no intensive new labs. | Review mistakes and rest. If sitting the exam later, keep the final day before the exam light. |

### Final troubleshooting gauntlet
In a disposable lab, reproduce and repair these faults:
- `CrashLoopBackOff`.
- `ImagePullBackOff`.
- Deployment has no available replicas.
- Service has no usable endpoints.
- DNS lookup fails.
- NetworkPolicy blocks expected traffic.
- PVC remains Pending.
- Pod cannot schedule.
- Container is OOMKilled.
- RBAC returns `Forbidden`.
- Node is NotReady.
- Control-plane/API connectivity issue in a kubeadm lab.

For every incident, prove the recovery. A changed YAML file or successful `kubectl apply` is not sufficient if the workload is still unhealthy.

### Personal readiness targets
These are **study targets**, not official pass-score guarantees:
- [ ] At least 80% on two consecutive timed mocks.
- [ ] Finish mocks within the full two-hour limit.
- [ ] No recurring, unexplained mistakes in the error log.
- [ ] Verify task completion rather than assuming commands succeeded.
- [ ] Perform common tasks from memory and use official documentation efficiently where permitted.
- [ ] Confirm exam version, environment, check-in requirements and allowed resources from current official instructions.

If you do not meet the targets, extend practice before booking or sitting the exam. A calendar date is not a reason to take the exam before you are ready.

---

## 5. High-value command patterns

These are examples to practise and adapt, not commands to paste blindly. Confirm the correct namespace, object names, container names and context.

### Generate YAML quickly
```bash
kubectl create deployment web --image=nginx --dry-run=client -o yaml
kubectl run test --image=busybox:1.36 --restart=Never --dry-run=client -o yaml
kubectl expose deployment web --port=80 --target-port=80 --dry-run=client -o yaml
kubectl explain deployment.spec
kubectl explain pod.spec.containers
```

### Diagnose workloads
```bash
kubectl get pods -A -o wide
kubectl describe pod <pod> -n <namespace>
kubectl logs <pod> -n <namespace>
kubectl logs <pod> -n <namespace> --previous
kubectl get events -n <namespace> --sort-by=.metadata.creationTimestamp
kubectl rollout status deployment/<name> -n <namespace>
kubectl rollout history deployment/<name> -n <namespace>
```

### Networking and Services
```bash
kubectl get svc,endpointslices -A
kubectl describe svc <service> -n <namespace>
kubectl get networkpolicy -A
kubectl get pods -n <namespace> --show-labels
kubectl exec -it <debug-pod> -n <namespace> -- sh
```

Use a debug image with the required tools available. `curl`, `dig`, `nslookup`, `ip` and `ss` are not installed in every container image.

### Storage
```bash
kubectl get pv,pvc,storageclass
kubectl describe pvc <claim> -n <namespace>
kubectl describe pv <volume>
kubectl get events -n <namespace> --sort-by=.metadata.creationTimestamp
```

### RBAC
```bash
kubectl get role,rolebinding -n <namespace>
kubectl get clusterrole,clusterrolebinding
kubectl auth can-i get pods -n <namespace>
kubectl auth can-i create deployments --as=<user> -n <namespace>
```

### Cluster and node checks
```bash
kubectl get nodes -o wide
kubectl describe node <node>
kubectl get componentstatuses
kubectl get pods -n kube-system -o wide
kubectl config view
kubectl config current-context
```

Note: `kubectl get componentstatuses` is deprecated/removed in newer Kubernetes versions and is not a reliable universal health check. Prefer node conditions, system Pods, events and the supported health checks available in your environment.

---

## 6. Exam execution strategy

The CKA is a practical, command-line exam. The official page currently states a two-hour duration. Read the current candidate handbook and exam tips before test day.

### During the exam
1. Read each task carefully; note the exact cluster/context, namespace, object names and required end state.
2. Switch context only when required, then verify the current context.
3. Start with tasks you can complete accurately and quickly.
4. Use imperative commands to generate YAML when useful, then edit the generated manifest.
5. Verify the resulting object and its health.
6. If blocked, collect evidence and move on rather than spending too long on one task.
7. Return to incomplete tasks when time permits.
8. Avoid destructive commands unless the task requires them and the target is confirmed.

### Allowed resources
The exact allowed-resource rules can change. The Linux Foundation currently describes allowed resources in its certification FAQ and links to the official policy. Verify the policy close to exam day. Do not assume personal notes, bookmarks, arbitrary websites, or third-party help are permitted. Practise solving tasks without relying on resources that will not be available.

### Final 24-hour checklist
- [ ] Review the latest CKA curriculum and exam version.
- [ ] Check identity, check-in, room, workstation and network requirements.
- [ ] Review permitted documentation/resources.
- [ ] Check your typing, terminal, editor and copy/paste workflow.
- [ ] Review the mistake log, not an entire course.
- [ ] Sleep adequately; avoid intensive last-minute cramming.

---

## 7. Weekly tracker

Mark a week complete only when the labs and completion gate are done.

- [ ] **Week 1 (17–23 Oct):** CLI, YAML, workloads and rollouts.
- [ ] **Week 2 (24–30 Oct):** resources, probes, scheduling and autoscaling.
- [ ] **Week 3 (31 Oct–6 Nov):** Services, DNS, NetworkPolicy and ingress.
- [ ] **Week 4 (7–13 Nov):** storage, ServiceAccounts and RBAC.
- [ ] **Week 5 (14–20 Nov):** kubeadm, control plane, etcd and cluster lifecycle.
- [ ] **Week 6 (21–27 Nov):** troubleshooting, Helm, Kustomize, CRDs and operators.
- [ ] **Week 7 (28 Nov–4 Dec):** two timed practice attempts and remediation.
- [ ] **Week 8 (5–11 Dec):** final mocks, weak areas and exam readiness.

## 8. Source-of-truth links

Re-check these shortly before the exam because curriculum details, exam versions and policies can change.

- CNCF CKA certification page: https://www.cncf.io/training/certification/cka/
- Linux Foundation CKA page: https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/
- Linux Foundation certification FAQ: https://training.linuxfoundation.org/about/faqs/certification-faq/
- Kubernetes documentation: https://kubernetes.io/docs/home/
- Kubernetes kubectl reference: https://kubernetes.io/docs/reference/kubectl/
- Kubernetes tasks: https://kubernetes.io/docs/tasks/
- Killercoda labs: https://killercoda.com/kubernetes
- Killer Shell: https://killer.sh/

**Final principle:** Passing CKA depends on solving practical tasks accurately under time pressure. Use documentation to learn, but use repeated hands-on practice to build speed. Prioritize troubleshooting (30%), cluster administration (25%) and networking (20%), while maintaining enough workload and storage practice to avoid losing straightforward marks.
