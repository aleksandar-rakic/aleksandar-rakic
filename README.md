<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:1F6FEB&height=180&section=header&text=Aleksandar%20Raki%C4%87&fontSize=44&fontColor=ffffff&animation=fadeIn&fontAlignY=34&desc=Senior%20Platform%20Engineer%20%C2%B7%20AWS%20%C2%B7%20Kubernetes%20%C2%B7%20Cloud%20Security&descAlignY=56&descSize=18" alt="Aleksandar Rakić, Senior Platform Engineer" />

<a href="https://github.com/aleksandar-rakic/aws-security-hub-auto-remediation"><img src="https://readme-typing-svg.demolab.com/?font=JetBrains+Mono&weight=500&size=17&duration=3200&pause=900&color=58A6FF&center=true&vCenter=true&width=640&lines=Secure-by-default+AWS+%26+EKS+platforms;Security+findings+fixed+in+seconds%2C+not+sprints;Terraform+%C2%B7+GitOps+%C2%B7+private+clusters+%C2%B7+observability;PhD+research%3A+ML+for+network+attack+detection" alt="Secure-by-default AWS and EKS platforms" /></a>

<p>
<a href="https://www.linkedin.com/in/rakic-aleksandar"><img src="https://img.shields.io/badge/LinkedIn-rakic--aleksandar-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://www.kaggle.com/aleksandarraki"><img src="https://img.shields.io/badge/Kaggle-aleksandarraki-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white" alt="Kaggle" /></a>
<a href="https://orcid.org/0009-0002-6324-8532"><img src="https://img.shields.io/badge/ORCID-0009--0002--6324--8532-A6CE39?style=for-the-badge&logo=orcid&logoColor=white" alt="ORCID" /></a>
<img src="https://img.shields.io/badge/Belgrade%2C_Serbia-1F6FEB?style=for-the-badge&logo=googlemaps&logoColor=white" alt="Belgrade, Serbia" />
</p>

</div>

## 👋 About

I build and run **AWS and Kubernetes platforms that are secure by default and quiet to operate**: multi-account AWS and EKS in Terraform and CDKTF, GitOps delivery, private cluster access, and the security controls around all of it.

**11+ years** in software and production systems. I started with ten years of backend engineering, including payment and banking systems, which helps when an incident crosses from the cluster into the application code. I hold an **MSc in Information Technology and Cyber Security** (University of Belgrade) and I am a **doctoral student** there, researching machine learning for network attack detection.

## 🛠️ What I work on

- **Kubernetes on AWS:** EKS fleets, version upgrades across many clusters, Karpenter, Cilium, add-on lifecycle
- **Infrastructure as code:** Terraform and CDKTF (TypeScript) for multi-account AWS, reviewed and applied from CI
- **Delivery:** GitOps with Argo CD and Flux, Helm, GitHub Actions with OIDC and in-cluster runners for private EKS APIs
- **Cloud security:** Security Hub and GuardDuty remediation, service control policies, SSO groups mapped to Kubernetes RBAC, TLS / mTLS
- **Observability:** Prometheus, Grafana, Mimir, Loki, Tempo and Alloy, alerting that a person can act on

## ⭐ Featured: Security Hub auto-remediation

<a href="https://github.com/aleksandar-rakic/aws-security-hub-auto-remediation"><b>aws-security-hub-auto-remediation</b></a> fixes failed AWS Security Hub controls across an AWS Organization within seconds of detection and writes every decision back onto the finding. Service control policies stop accounts from switching detection or remediation off.

```mermaid
flowchart LR
    SH["Security Hub<br/>FAILED finding"] --> EB["EventBridge"] --> L["Remediation<br/>Lambda"]
    L -- "assume role" --> M["Member accounts<br/>S3 · EC2 · RDS · KMS · SQS · ECR"]
    L -- "RESOLVED / NOTIFIED + note" --> SH
    L -. "failed after retries" .-> DLQ["Dead-letter queue<br/>+ alarm"]
    SCP["SCP guardrails"] -. "protect detection<br/>and remediation" .-> M
```

<table>
<tr>
<td width="50%" valign="top">

**What it covers**

- 16 Security Hub controls: public S3 and snapshots, open admin ports, IMDSv2, TLS-only buckets, encryption, key rotation
- GuardDuty response: isolate a compromised instance and keep forensic snapshots
- Cross-account through one least-privilege member role

</td>
<td width="50%" valign="top">

**Why it is safe to run**

- Dry run by default, per-resource opt-out tag
- Checks before acting: no IMDSv2 switch while IMDSv1 is still used, no emptied default group while it is attached
- 58 Python tests (moto) and Terraform tests, no AWS account needed

</td>
</tr>
</table>

## 📌 Projects

| Project | What it shows | Stack |
|:--|:--|:--|
| [**aws-security-hub-auto-remediation**](https://github.com/aleksandar-rakic/aws-security-hub-auto-remediation) | Event-driven remediation of Security Hub findings with SCP guardrails, an operations runbook and safe rollout | ![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white) ![Terraform](https://img.shields.io/badge/-Terraform-7B42BC?logo=terraform&logoColor=white) ![AWS](https://img.shields.io/badge/-AWS-232F3E?logo=amazonwebservices&logoColor=white) |
| [**eks-private-api-github-runners**](https://github.com/aleksandar-rakic/eks-private-api-github-runners) | Taking the EKS API private without breaking CI: OIDC for AWS, in-cluster runners for Kubernetes, a bootstrap window for new clusters | ![Kubernetes](https://img.shields.io/badge/-EKS-326CE5?logo=kubernetes&logoColor=white) ![Terraform](https://img.shields.io/badge/-Terraform-7B42BC?logo=terraform&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/-Actions-2088FF?logo=githubactions&logoColor=white) |
| [**cyber-attack-dataset-arp-syn-ping-flood**](https://github.com/aleksandar-rakic/cyber-attack-dataset-arp-syn-ping-flood) | Rebuilding a published network-attack dataset: original units recovered, leakage-free split, baselines | ![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white) ![scikit-learn](https://img.shields.io/badge/-scikit--learn-F7931E?logo=scikitlearn&logoColor=white) ![DOI](https://img.shields.io/badge/DOI-10.34740%2Fkaggle%2Fds%2F5620663-blue) |
| [**wordpress-malware-persistence-case-study**](https://github.com/aleksandar-rakic/wordpress-malware-persistence-case-study) | Incident response write-up: a self-restoring WordPress infection, its persistence chain, defanged indicators | ![Security](https://img.shields.io/badge/-Incident_response-B31B1B?logo=letsencrypt&logoColor=white) ![PHP](https://img.shields.io/badge/-PHP-777BB4?logo=php&logoColor=white) |

## 🧰 Tech stack

<p align="center">
<img src="https://skillicons.dev/icons?i=aws,kubernetes,terraform,docker,linux,githubactions,prometheus,grafana,kafka,postgres,redis,nginx,python,ts,bash,php,git&perline=9" alt="AWS, Kubernetes, Terraform, Docker, Linux, GitHub Actions, Prometheus, Grafana, Kafka, PostgreSQL, Redis, nginx, Python, TypeScript, Bash, PHP, Git" />
</p>

| Area | Tools |
|:-----|:------|
| **Cloud and Kubernetes** | AWS (multi-account, Organizations), EKS, Helm, Karpenter, Cilium, Docker, Linux |
| **Infrastructure as code** | Terraform, CDKTF (TypeScript), Terraform tests, tflint |
| **Delivery** | Argo CD, Flux, GitHub Actions, Actions Runner Controller |
| **Security** | Security Hub, GuardDuty, SCPs, IAM and IAM Identity Center, Kubernetes RBAC, TLS / mTLS |
| **Observability** | Prometheus, Grafana, Mimir, Loki, Tempo, Grafana Alloy |
| **Data and messaging** | Kafka (Strimzi), Aurora PostgreSQL, Valkey / Redis |
| **Languages** | Python, TypeScript, Bash, PHP |

## 🔬 Research and open data

- **Cyber Attack Dataset: ARP, SYN, PING Flood (v3).** One 53-minute lab capture of 439,171 frames in original Wireshark units, with a chronological train/test split and the raw attack packets. [Kaggle](https://www.kaggle.com/datasets/aleksandarraki/cyber-attack-dataset-arp-syn-ping-flood) · DOI [10.34740/kaggle/ds/5620663](https://doi.org/10.34740/kaggle/ds/5620663)
- **Detection of ARP spoofing, SYN and PING flood attacks using machine learning models.** Info M, 2024. [Paper](https://infom.fon.bg.ac.rs/index.php/infom/article/view/2678)
- **Detecting ransomware applying machine learning algorithms.** With D. Simić. SYM-OP-IS 2024. DOI [10.24867/symopis-2024-51-024](https://doi.org/10.24867/symopis-2024-51-024)

## 💬 Talk to me about

Running EKS at scale without drama · moving clusters to private endpoints · turning security findings into automation · ML for intrusion detection

<div align="center">

<a href="https://www.linkedin.com/in/rakic-aleksandar"><img src="https://img.shields.io/badge/Say_hello_on_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="Say hello on LinkedIn" /></a>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1F6FEB,50:161B22,100:0D1117&height=100&section=footer" alt="" />

</div>
