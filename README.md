<p align="center">
  <img src="./assets/banner.svg" alt="Saim Zaib · Cloud · DevOps · DevSecOps" width="100%" />
</p>

<p align="center">
  <a href="https://github.com/floci-io/floci/pulls?q=is%3Apr+author%3Asaimcyber+is%3Amerged"><img src="https://img.shields.io/badge/floci-2_merged_PRs-3fb950?style=flat-square&logo=github&logoColor=white" alt="floci: 2 merged PRs" /></a>
  <br />
  <img src="https://img.shields.io/badge/OCI-Certified_DevOps_Professional-C74634?style=flat-square&logo=oracle&logoColor=white" alt="OCI Certified DevOps Professional" />
  <img src="https://img.shields.io/badge/OCI-Architect_Associate-C74634?style=flat-square&logo=oracle&logoColor=white" alt="OCI Architect Associate" />
  <img src="https://img.shields.io/badge/Google_Cloud-Cybersecurity_Certificate-4285F4?style=flat-square&logo=googlecloud&logoColor=white" alt="Google Cloud Cybersecurity Certificate" />
  <br />
  <img src="https://img.shields.io/badge/AWS_Student_Builders-Founding_President-FF9900?style=flat-square&logo=amazonwebservices&logoColor=white" alt="AWS Student Builders Community, Founding President" />
  <img src="https://img.shields.io/badge/Positive_Hack_Camp_2026-1_of_800%2B_selected-2DD4BF?style=flat-square" alt="Positive Hack Camp 2026" />
</p>

I build cloud platforms where the pipeline is the security control: nothing reaches production unscanned, unsigned or untracked.

My work starts from a hard constraint: a 4 GB GPU, zero stored secrets, a cluster that must reject what it cannot verify. It ends as a system where Terraform defines the infrastructure, GitOps ships the change, and admission policy has the last word.

Currently: BS Cyber Security at FAST-NUCES Islamabad, founding President of the campus AWS Student Builders Community, and contributor to [floci](https://github.com/floci-io/floci), the open-source local AWS emulator. Previously: DevSecOps Officer at Google Developer Groups on Campus.

[Portfolio](https://saimzaib.tech) · [LinkedIn](https://linkedin.com/in/saimzaib) · [Email](mailto:saimzaib.official@gmail.com)

## What I bring

| Cloud & platform | DevSecOps | Community & leadership |
|---|---|---|
| AWS in Terraform: VPC, ALB + Auto Scaling, private RDS, Lambda, least-privilege IAM | CI gates that block CRITICAL CVEs with Trivy before an image is pushed | Founded the campus AWS Student Builders chapter with AWS approval |
| Kubernetes with Helm and Argo CD GitOps across dev, staging and prod | Keyless cosign signing, SBOMs, and Kyverno rejecting unsigned images at admission | Hands-on workshops that take members from guided labs to their own deployments |
| Prometheus and Grafana with SLO, GPU, cost and security alerting | GitHub OIDC to AWS IAM, so pipelines hold zero long-lived secrets | Mentoring on Docker, Kubernetes and pipeline automation |

## How I take a system to production

The same discipline goes into every milestone I ship:

1. **write down what "done" means** as an acceptance test before building;
2. **make the pipeline enforce it**: scan, sign, attest, then admit;
3. **try to break it**: chaos experiments, load tests and a threat model, then a postmortem for whatever broke.

## Open-source contributions

**[floci](https://github.com/floci-io/floci)** (open-source local AWS emulator): 2 merged

| Area | What was broken | PR |
|---|---|---|
| EventBridge | API destinations couldn't deliver to an endpoint whose certificate came from a private CA, because Floci's HTTPS clients trusted only the roots built into the binary. Added `FLOCI_TLS_EXTRA_CA_PATH` and assembled outbound trust in one place, so JWT authorizers and AppSync OIDC accept those CAs too | [#7850](https://github.com/floci-io/floci/pull/7850) |
| SNS | HTTPS subscriptions to a private-CA endpoint failed for the same reason; they now share the same trust | [#8063](https://github.com/floci-io/floci/pull/8063) |

For #7850 I traced the failure to the HTTP client, proposed a design on the issue, agreed the scope with the maintainers, and tested against a local HTTPS server with a throwaway CA.

## Palisade, by the numbers

**[Palisade](https://github.com/saimcyber/palisade)**: a secure, self-hosted LLM inference platform. vLLM on a 4 GB GPU in k3d Kubernetes, behind an OpenAI-compatible FastAPI gateway.

| Area | What I built | Result |
|---|---|---|
| Supply chain | GitHub Actions with a Trivy gate, keyless cosign signing and SBOM | CRITICAL CVEs cut from **3 → 0** |
| Identity | GitHub OIDC federated to AWS IAM | **Zero** stored secrets |
| Admission | Kyverno policies plus default-deny NetworkPolicy | Unsigned images **rejected** at the cluster door |
| Multi-tenancy | Redis-backed per-tenant rate limits, token budgets, audit log, prompt guard | Each tenant held to its own budget |
| Observability | Prometheus and Grafana | **4** dashboards, **7** alerts (SLO, GPU, cost, security) |
| Resilience | Chaos engineering and k6 load tests, load shedding | **5** bugs fixed, including a Kyverno bypass |
| Decisions | STRIDE threat model, SLO, runbook, blameless postmortem | **27** ADRs and a public devlog |

Shipped in six acceptance-tested milestones, Sep to Nov 2026.

## Selected projects

| Problem | System | Outcome |
|---|---|---|
| Teams want a private LLM but can't trust what runs in the cluster | **[Palisade](https://github.com/saimcyber/palisade)**: Helm + Argo CD GitOps, signed images, Kyverno admission, tenant budgets | A self-hosted inference platform with a verifiable supply chain |
| Images ship to production without anyone checking them | **[SecureKubeOps](https://github.com/saimcyber/SecureKubeOps)** + **[securekubeops-infra](https://github.com/saimcyber/securekubeops-infra)**: two-repo GitOps pipeline, non-root images, Trivy scanning, SHA tags promoted dev → staging → prod | Every deploy is scanned, traceable and reproducible |
| Clicking through the AWS console doesn't scale or audit | **[AWS-Learning-Journey](https://github.com/saimcyber/AWS-Learning-Journey)**: VPC with public/private subnets and NAT, ALB + ASG, private RDS, SNS → SQS fan-out, Lambda | Infrastructure that is reviewed, versioned and rebuilt from code |
| Juniors don't know what to learn next in cloud security | **[cloud-security-roadmap](https://github.com/saimcyber/cloud-security-roadmap)**: a 26-week, gate-driven path of hands-on labs | A clear route from fundamentals to DevSecOps work |
| A monolith can't isolate access per service | **AwareNet** (private): 10+ Python microservices in Docker behind a REST gateway with JWT and RBAC | Each service is independently deployed and access-controlled |
| An off-grid solar system fails silently | **[solarwatch](https://github.com/saimcyber/solarwatch)**: polls the inverter and sends an hourly heartbeat and alerts to WhatsApp | Problems surface on my phone, not when the lights go out |

## Focus areas

- **Software supply chain security**: scanning, signing, SBOMs and admission control.
- **Platform engineering on Kubernetes**: GitOps, policy-as-code and observability that pages on the right thing.
- **Cloud infrastructure as code**: AWS in Terraform with least-privilege IAM by default.
- **Open source in the cloud tooling I use**: fixing real bugs upstream, starting with floci.

<p>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white" alt="AWS" />
  <img src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white" alt="Terraform" />
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white" alt="Kubernetes" />
  <img src="https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white" alt="Helm" />
  <img src="https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white" alt="Argo CD" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions" />
  <img src="https://img.shields.io/badge/Trivy-1904DA?style=flat-square&logo=aqua&logoColor=white" alt="Trivy" />
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white" alt="Prometheus" />
  <img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white" alt="Grafana" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white" alt="Bash" />
  <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux" />
</p>

Always happy to talk about Kubernetes security, CI/CD supply chains, or getting a student community shipping real cloud projects. Reach me on [LinkedIn](https://linkedin.com/in/saimzaib) or by [email](mailto:saimzaib.official@gmail.com).
