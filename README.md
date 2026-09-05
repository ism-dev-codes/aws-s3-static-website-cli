<div align="center">

# ☁️ Hospedagem de Site Estático no Amazon S3 via AWS CLI & Automação de Deploy

![AWS](https://img.shields.io/badge/AWS-AWS%20re%2FStart-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-Static%20Hosting-569A31?style=for-the-badge&logo=amazons3&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-Access%20Control-DD344C?style=for-the-badge&logo=amazonaws&logoColor=white)
![Linux Shell](https://img.shields.io/badge/Bash-Shell%20Scripting-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)

<p align="center">
  <b>Implantação de um site estático no Amazon S3 utilizando a interface de linha de comando (AWS CLI), gerenciamento de permissões com IAM, configuração de ACLs e criação de scripts Shell de automação/sincronização.</b>
</p>

</div>

---

## 📌 Visão Geral do Projeto & Cenário de TI

Neste projeto de infraestrutura em nuvem, simulei uma demanda de suporte e administração de sistemas para uma empresa fictícia (*Café & Bakery*). O objetivo foi migrar e disponibilizar a hospedagem do site institucional estático para o **Amazon Simple Storage Service (Amazon S3)** utilizando comandos via **AWS CLI** executados a partir de uma instância Amazon EC2 conectada via **AWS Systems Manager (SSM)**.

Além da hospedagem, estruturei o gerenciamento de controle de acesso (IAM/Bucket Policies/ACLs) e automatizei o processo de deploy contínuo do site utilizando scripts em **Bash** para otimizar o fluxo de atualizações.

### 🎯 Habilidades Demonstradas
* **Administração de Sistemas Linux & AWS CLI:** Execução de comandos de gerenciamento de nuvem diretamente via terminal.
* **Segurança e Gestão de Identidades (IAM):** Criação de usuários, login profiles e associação de políticas gerenciadas (`AmazonS3FullAccess`).
* **Hospedagem e Redes na AWS:** Configuração de endpoints de sites estáticos no S3 e ajuste fino de propriedades como *Block Public Access* e *ACLs*.
* **Automação de Suporte/Operações:** Criação de scripts executáveis `.sh` usando `aws s3 cp` e otimização de transferência diferencial com `aws s3 sync`.

---

## 📐 Arquitetura da Solução

```text
 [ Usuário / Cliente ]
           │ (HTTP)
           ▼
┌────────────────────────────────────────────────────────┐
│ Amazon S3 Bucket (Hospedagem de Site Estático)         │
│  ├── index.html                                        │
│  ├── css/                                              │
│  └── images/                                           │
└────────────────────────────────────────────────────────┘
           ▲
           │ (Upload via AWS CLI / Shell Script)
┌────────────────────────────────────────────────────────┐
│ Instância Amazon EC2 (Amazon Linux)                    │
│  ├── Acesso via SSM Session Manager                    │
│  └── Script de Automação: update-website.sh            │
└────────────────────────────────────────────────────────┘
