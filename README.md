# 🚀 Introdução ao Terraform com AWS (Curso DevOps Básico ADA)

Este repositório documenta e demonstra os conhecimentos adquiridos durante a trilha de Introdução ao Terraform, como parte do curso de DevOps Básico da ADA. O objetivo principal foi explorar os fundamentos de Infraestrutura como Código (IaC) e, especificamente, o uso do Terraform para provisionar recursos na AWS.

## 🌟 O que foi abordado neste curso/projeto:

*   **Introdução à IaC e Terraform:** Conceitos fundamentais de Infraestrutura como Código, o que é Terraform e seus benefícios.
*   **Workflow e Lifecycle do Terraform:** Entendimento do ciclo de vida de um projeto Terraform (`init`, `plan`, `apply`, `destroy`).
*   **Providers e Block Types:** Como configurar provedores (neste caso, AWS) e os diferentes blocos de configuração (`resource`, `data`, `module`, `variable`, `output`).
*   **Variáveis e Funções:** Uso de variáveis para parametrizar configurações e tornar o código mais reutilizável.
*   **State File:** A importância do `terraform.tfstate` para o gerenciamento do estado da infraestrutura.
*   **Módulos:** Conceito e aplicação de módulos para organizar e reutilizar blocos de configuração.
*   **Boas Práticas:** Padrões e recomendações para escrever código Terraform legível e mantenível.
*   **Edições do Terraform:** Diferenças entre Terraform CLI (Free), Terraform Cloud e Terraform Enterprise.

## 🛠️ Recursos AWS Provisionados:

Como parte dos exercícios práticos, este projeto demonstra o provisionamento de:

1.  **VPC (Virtual Private Cloud):** Uma rede virtual isolada na AWS, com subnets públicas e privadas, NAT Gateway e VPN Gateway, utilizando o módulo `terraform-aws-modules/vpc/aws`.
2.  **Instância EC2:** Uma máquina virtual Ubuntu (22.04 LTS) provisionada dentro da VPC criada.

## 📁 Estrutura do Projeto:

```bash
.
├── .gitignore                 # Arquivos a serem ignorados pelo Git
├── data.tf                    # Definição de fontes de dados (ex: AMI ID)
├── main.tf                    # Configurações principais dos recursos (VPC e EC2)
├── outputs.tf                 # Saídas importantes do projeto (ex: IP Privado da EC2)
├── providers.tf               # Configuração do provedor AWS
├── settings.tf                # Configurações do Terraform (versão do provedor)
├── terraform-dev.tfvars       # Variáveis para ambiente de desenvolvimento
├── variables.tf               # Declaração das variáveis do projeto
└── README.md                  # Este arquivo


## ⚙️ Pré-requisitos:

Antes de executar este projeto, certifique-se de ter os seguintes itens configurados:

*   **AWS Account:** Uma conta da Amazon Web Services.
*   **AWS CLI:** Configurador e autenticado com credenciais que tenham permissão para criar recursos EC2 e VPC.
*   **Terraform CLI:** Instalado na sua máquina (versão 1.x ou superior).
*   **VS Code (com extensão Terraform):** Recomendado para melhor experiência de desenvolvimento.

## ▶️ Como Executar o Projeto:

Siga os passos abaixo para provisionar a infraestrutura na sua conta AWS:

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/SEU_USUARIO/terraform-ada-intro-devops.git
    cd terraform-ada-intro-devops
    ```
    *Lembre-se de substituir `SEU_USUARIO` pelo seu nome de usuário no GitHub.*

2.  **Inicialize o Terraform:**
    Este comando baixa os plugins dos provedores necessários.
    ```bash
    terraform init
    ```

3.  **Valide a configuração:**
    Verifica se o código Terraform está sintaticamente correto.
    ```bash
    terraform validate
    ```

4.  **Visualize o plano de execução:**
    Gera um plano de execução mostrando o que o Terraform irá criar, modificar ou destruir.
    ```bash
    terraform plan -var-file="terraform-dev.tfvars"
    ```

5.  **Aplique as mudanças:**
    Executa o plano e provisiona os recursos na AWS. **Cuidado ao executar este comando, pois ele cria recursos na sua conta AWS que podem gerar custos.**
    ```bash
    terraform apply -var-file="terraform-dev.tfvars"
    ```
    Confirme com `yes` quando solicitado.

6.  **Verifique as saídas:**
    Após a aplicação bem-sucedida, o Terraform exibirá os `outputs` definidos, como o IP privado da instância EC2.
    ```bash
    terraform output ip_privado
    ```

## 🗑️ Como Destruir a Infraestrutura:

Para evitar custos indesejados, é fundamental destruir os recursos após terminar de usá-los.

```bash
terraform destroy -var-file="terraform-dev.tfvars"
Confirme com yes quando solicitado

## 🔗 Referências Úteis:

Durante o desenvolvimento deste laboratório, as seguintes documentações foram consultadas e são recursos valiosos para aprofundar o conhecimento em Terraform e AWS:

* **AWS Provider Documentation:** Documentação oficial do provedor AWS para Terraform, detalhando todos os recursos e datasources disponíveis.
    [https://registry.terraform.io/providers/hashicorp/aws/latest](https://registry.terraform.io/providers/hashicorp/aws/latest)

* **Terraform AWS VPC Module:** Documentação do módulo oficial da HashiCorp para provisionamento de VPCs na AWS, utilizado neste projeto.
    [https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest)

* **Terraform Language - Modules:** Documentação sobre o uso e criação de módulos na linguagem Terraform, um conceito fundamental para projetos escaláveis.
    [https://developer.hashicorp.com/terraform/language/modules](https://developer.hashicorp.com/terraform/language/modules)
