## Diferença entre IaaS e PaaS na GCP
### IaaS (Infrastructure as a Service) 
Fornece infraestrutura de TI virtualizada, como servidores, 
redes, armazenamento e sistemas operacionais. O usuário tem controle total sobre a configuração, mas 
precisa gerenciar o sistema operacional, atualizações e segurança.
 - Compute Engine
 - Cloud Storage
 - VPC
 - Cloud Load Balacing

### PaaS (Platform as a Service) 
Fornece uma plataforma gerenciada, onde o usuário se preocupa apenas com o
 desenvolvimento e implantação de aplicativos, sem precisar gerenciar servidores, SOs ou
  infraestrutura subjacente.
 - App Engine
 - Cloud Functions
 - Cloud Run
 - Firebase

## Resumo das Diferenças

| Característica        | IaaS (Infrastructure as a Service)       | PaaS (Platform as a Service)         |
|----------------------|------------------------------------|--------------------------------|
| **Nível de controle** | Alto (gerencia SO, rede, segurança) | Médio/Baixo (foca apenas na aplicação) |
| **Gerenciamento**     | Hardware virtual, SO, configurações | Apenas código e lógica da aplicação |
| **Escalabilidade**    | Manual ou semi-automatizado         | Totalmente automatizado |
| **Tempo de configuração** | Demorado (instalação e manutenção necessárias) | Rápido (deploy simplificado) |
| **Exemplo na GCP**   | Compute Engine, Cloud Storage, VPC  | App Engine, Cloud Run, BigQuery |

## SaaS (Software as a Service) 
É um modelo de computação em nuvem onde os usuários acessam aplicativos através da internet, sem necessidade de instalação ou gerenciamento de infraestrutura. O provedor do serviço cuida de atualizações, manutenção, segurança e escalabilidade, permitindo que os usuários simplesmente utilizem o software.
 - Google Worspace
 - Google Cloud Identity
 - BigQuery
 - Google Analytics
 - Google Meets


 ## Zona e Região
 Região é uma área geográfica específica que contém várias Zonas.
 ✔ Localização geográfica única → Cada região representa um país ou cidade específica.
✔ Composta por múltiplas Zonas → Normalmente, tem três ou mais zonas dentro dela.
✔ Baixa latência → Todos os recursos dentro de uma mesma região têm comunicação rápida.
Exemplo de Regiões na GCP:

us-central1 → Iowa (EUA)
europe-west1 → Bélgica
asia-east1 → Taiwan

Zona é um data center físico dentro de uma Região.
✔ Cada Zona pertence a uma Região → Identificada como região-letra (ex: us-central1-a).
✔ Recursos dentro da mesma Zona têm menor latência entre si.
✔ Se uma Zona falhar, outras Zonas da mesma Região podem assumir a carga.
✔ Cada Zona tem recursos independentes (máquinas virtuais, discos, redes, etc.).

Exemplo de Zonas na GCP:
Na região us-central1 (Iowa, EUA), existem múltiplas zonas:
us-central1-a
us-central1-b
us-central1-c

## Hierarquia de recursos
📌 Organização (Organization)
 ├── 📂 Pasta (Folder) [Opcional]
 │    ├── 📂 Subpastas (Subfolders) [Opcional]
 │    │    ├── 📦 Projetos (Projects)
 │    │    │    ├── 🖥️ Recursos (Compute Engine, Cloud Storage, Cloud SQL, etc.)
 │    │    │
 │    │    ├── 📦 Projetos (Projects)
 │    │
 │    ├── 📦 Projetos (Projects)
 │
 ├── 📦 Projetos (Projects)
      ├── 🖥️ Recursos (VMs, Storage, BigQuery, etc.)

### Organização
Nível mais alto na hierarquia, representando a empresa ou domínio.

✔ Associado a um domínio do Google Workspace ou Cloud Identity.
✔ Controla políticas e permissões herdadas para todos os recursos abaixo.
✔ É obrigatório para contas corporativas, mas opcional para contas individuais.

Exemplo:

mycompany.com (Organização para todos os projetos da empresa)      

### Pastas
Agrupam projetos e subpastas dentro da Organização.

✔ Permitem segregar departamentos, equipes ou ambientes (Dev, Staging, Prod).
✔ As permissões e políticas podem ser aplicadas a um grupo de projetos.

Exemplo:

Departamento de TI
📂 Desenvolvimento
📂 Produção
📂 Equipe de Dados

### Projetos
Unidade fundamental na GCP para organizar recursos.

✔ Todos os recursos (VMs, Storage, APIs, etc.) devem estar dentro de um projeto.
✔ Cada projeto tem um ID único globalmente e um número de projeto.
✔ Projetos podem ser excluídos ou migrados para outras pastas.

Exemplo:

mycompany-prod
data-analytics-project
website-hosting

### Recursos
Serviços individuais criados dentro dos projetos.

✔ Representam máquinas virtuais, bancos de dados, armazenamento, etc.
✔ Herda permissões e políticas do projeto onde está localizado.

Exemplo:

Compute Engine → Instâncias de máquinas virtuais.
Cloud Storage → Buckets de armazenamento.
Cloud SQL → Banco de dados gerenciado.
BigQuery → Plataforma de análise de dados.

## Atributos de Projeto
Cada projeto na Google Cloud possui três identificadores principais:

| Campo            | Descrição                                                                                   | Exemplo             |
|-----------------|--------------------------------------------------------------------------------------------|---------------------|
| **Project ID**   | 🔹 **Único globalmente** <br> 🔹 **Definido pelo usuário ou gerado automaticamente** <br> 🔹 **Imutável após a criação** | `my-first-project` |
| **Project Name** | 🔹 **Nome amigável para identificação** <br> 🔹 **Pode ser alterado a qualquer momento** <br> 🔹 **Não precisa ser único** | `My First GCP Project` |
| **Project Number** | 🔹 **Número único gerado pelo Google Cloud** <br> 🔹 **Imutável** <br> 🔹 **Usado para APIs e billing** | `123456789012` |

---


### Exemplo de Projetos Criados na GCP

| Project ID         | Project Name            | Project Number |
|--------------------|------------------------|---------------|
| `my-first-project`  | My First GCP Project    | `123456789012`  |
| `data-analytics`    | Data Analytics Project  | `987654321098`  |
| `web-hosting-prod`  | Web Hosting - Production | `112233445566`  |
| `cloud-storage-app` | Cloud Storage Application | `334455667788`  |
| `bigquery-reports`  | BigQuery Reporting      | `556677889900`  |

---

### Explicação dos Campos
✔ **Project ID** → Um identificador **único e global**, gerado automaticamente ou definido pelo usuário. **Não pode ser alterado após a criação**.  
✔ **Project Name** → Nome amigável definido pelo usuário, **pode ser alterado a qualquer momento**.  
✔ **Project Number** → Um **identificador numérico único**, atribuído automaticamente pelo Google Cloud e **imutável**.

---

**Notas:**
- **Project ID** deve ser único em toda a Google Cloud e não pode ser reutilizado.  
- **Project Name** pode ser atualizado sem afetar configurações.  
- **Project Number** é útil para operações internas e APIs.  

## Roles e Policies
O IAM (Identity and Access Management) do Google Cloud é o sistema que controla quem pode acessar quais recursos dentro da plataforma. Ele funciona através de políticas (Policies) e papéis (Roles), garantindo segurança e um gerenciamento eficaz de permissões.

### O IAM tem três componentes principais:

- Identidade (Member): Representa quem recebe as permissões (usuários, grupos, contas de serviço ou domínios).
- Papel (Role): Conjunto de permissões atribuídas a uma identidade.
- Política IAM (Policy): Define quem pode fazer o quê em um recurso.

### Tipos de Roles
 - Papéis Predefinidos (Predefined Roles) – Recomendados
 
 Exemplos:
   - roles/storage.admin → Permite gerenciar buckets e objetos no Cloud Storage.
   - roles/bigquery.dataViewer → Concede permissão apenas para visualizar dados no BigQuery.
   - roles/compute.instanceAdmin → Permite gerenciar instâncias no Compute Engine.

 - Papéis Personalizados (Custom Roles) – Para maior controle
 - Papéis Básicos (Primitive Roles) – NÃO Recomendados

 ### Boas Práticas para Gerenciar IAM 
* Aplique o Princípio do Menor Privilégio → Conceda apenas as permissões necessárias.
* Prefira Roles Predefinidos ao invés de Primitive Roles → Para garantir mais segurança.
* Revise os acessos regularmente → Revogue permissões de usuários que não precisam mais delas.
* Utilize Grupos e Contas de Serviço → Em vez de atribuir permissões diretamente a usuários individuais.

## Cloud Identity
É a solução do Google Cloud Platform (GCP) para gerenciamento de identidades e acessos. Ele permite controlar usuários, grupos, dispositivos e permissões dentro de uma organização, garantindo segurança, conformidade e eficiência na administração de acessos.

### Usuários
São as identidades de pessoas dentro da organização, geralmente associadas a um e-mail corporativo (ex: maria@empresa.com).

✔ Permite autenticação centralizada com login único (SSO – Single Sign-On).
✔ Garante segurança com autenticação multifator (MFA).
✔ Controla permissões dentro da organização via IAM (Identity and Access Management).

### Grupos
Um grupo é um conjunto de usuários que compartilham as mesmas permissões e acessos a recursos.

✔ Facilita a administração de permissões → Em vez de atribuir acessos a cada usuário individualmente, o administrador pode conceder permissões a um grupo.
✔ Melhor controle de acessos → Exemplo: Grupo "Financeiro" pode acessar o BigQuery, enquanto "Desenvolvedores" têm permissões no Compute Engine.
✔ Integração com IAM → Grupos podem ser usados diretamente dentro de políticas IAM.

🔹 Exemplo de Grupo:

Grupo: dev-team@empresa.com
Membros: João, Maria, Pedro
Permissão: roles/compute.admin → O grupo tem acesso para administrar instâncias do Compute Engine.

### Dispositivos
O Cloud Identity gerencia dispositivos corporativos, garantindo que apenas dispositivos autorizados possam acessar os serviços da organização.

✔ Gerenciamento de dispositivos móveis (MDM - Mobile Device Management) → Controla acesso a partir de celulares e tablets.
✔ Aplicação de políticas de segurança → Exige criptografia de disco, senhas seguras, bloqueio remoto.
✔ Monitoramento e auditoria → Permite rastrear e bloquear dispositivos suspeitos.

🔹 Exemplo:
Se um funcionário perder o celular corporativo, o administrador pode bloquear o dispositivo remotamente para evitar acessos não autorizados.

### Aplicativos (Apps)
Gerencia quais aplicativos os usuários podem acessar dentro da organização.

✔ Integração com Google Workspace → Gmail, Drive, Docs, Sheets, Meet.
✔ Controle de acesso a aplicativos externos → Exemplo: Bloquear acesso a serviços não autorizados.
✔ SSO (Single Sign-On) → Usuários podem fazer login uma única vez e acessar vários sistemas corporativos sem precisar de várias senhas.

🔹 Exemplo:

A empresa define que apenas usuários autenticados via Cloud Identity podem acessar Slack, Trello e GitHub.
Qualquer tentativa de login externo será bloqueada.

## Maneiras de iteragir com o GCP
### Google Cloud CLI
A CLI oficial do GCP (gcloud) permite executar comandos para gerenciar recursos sem precisar acessar a interface gráfica.

✔ Útil para automação e scripts.
✔ Mais rápido que o console web para algumas tarefas repetitivas.
✔ Permite interagir com Compute Engine, Cloud Storage, IAM, Kubernetes, BigQuery e outros serviços.

### Cloud Shell 
O Cloud Shell é um terminal baseado na nuvem integrado ao Google Cloud Console. Ele permite executar comandos gcloud, kubectl, terraform, e outros sem precisar instalar nada localmente.

✔ Acesso imediato ao terminal sem configuração local.
✔ Inclui ferramentas pré-instaladas, como Python, Git, Terraform e kubectl.
✔ Ambiente persistente com armazenamento de 5GB gratuito.

### Google Cloud REST APIs
As APIs REST do Google Cloud permitem acessar e gerenciar recursos programaticamente, sem precisar usar a interface web ou CLI.

✔ Ideal para integração com sistemas externos e automação.
✔ Pode ser usada em Python, Java, Node.js, Go, C#, Ruby, etc.
✔ Utiliza chaves de API ou OAuth 2.0 para autenticação.

### Google Cloud Client Libraries (SDKs para Linguagens de Programação)
O GCP disponibiliza SDKs para diversas linguagens, facilitando o desenvolvimento de aplicações que interagem com seus serviços.

✔ Permite criar, gerenciar e monitorar serviços GCP diretamente no código.
✔ Reduz a complexidade do uso da API REST.
✔ Disponível para Python, Java, Go, Node.js, C#, Ruby e PHP.

### Terraform (Infraestrutura como Código - IaC)
O Terraform permite definir e provisionar infraestrutura na GCP usando arquivos de configuração.

✔ Automação e controle de infraestrutura em código.
✔ Ideal para DevOps e ambientes de produção escaláveis.
✔ Evita erros manuais e facilita replicação de ambientes.

## Deploying Applications
### Code
Nesta fase, os desenvolvedores escrevem e versionam o código-fonte da aplicação.

✔ Utilização de repositórios Git para versionamento e colaboração.
✔ Integração com ferramentas como Cloud Source Repositories, GitHub ou GitLab.
✔ Pode incluir revisões de código (code review) e scans de segurança antes do build.

🔹 Ferramentas no GCP:

Cloud Source Repositories → Repositório privado para armazenar código.
Artifact Registry → Armazena pacotes, imagens de contêiner e artefatos de build.

### Build
Aqui, o código-fonte é transformado em um artefato pronto para ser implantado.

✔ O código é compilado, empacotado e verificado.
✔ Pode incluir análise estática de código e testes unitários.
✔ Criação de imagens de contêiner para implantação em ambientes Kubernetes.

🔹 Ferramentas no GCP:

Cloud Build → Serviço de CI/CD que compila e gera artefatos automaticamente.
Container Registry / Artifact Registry → Armazena imagens de contêiner para Kubernetes.
Cloud Functions Build → Para aplicações serverless baseadas em funções

### Deploy
O software é implantado automaticamente ou sob demanda em um ambiente específico.

✔ Estratégias de deploy como blue-green, canary, rolling updates.
✔ Pode ser feito em máquinas virtuais, Kubernetes ou ambientes serverless.
✔ Controle de versões e rollback em caso de falha.

🔹 Ferramentas no GCP:

Cloud Run → Para rodar contêineres sem gerenciar servidores.
Google Kubernetes Engine (GKE) → Implantação escalável em Kubernetes.
App Engine → Plataforma serverless gerenciada para aplicações web.
Compute Engine → Para deploy em VMs personalizadas.

### Test
Última fase antes de liberar para produção, garantindo a confiabilidade da aplicação.

✔ Testes automatizados: unitários, integração, carga, segurança e regressão.
✔ Monitoramento e logging em produção para detectar problemas rapidamente.
✔ Automação de rollback caso falhas sejam detectadas.

🔹 Ferramentas no GCP:

Cloud Monitoring → Coleta métricas de desempenho.
Cloud Logging → Armazena e analisa logs da aplicação.
Cloud Trace → Identifica gargalos de performance.
Cloud Testing (Firebase Test Lab) → Teste automatizado para apps mobile.

### Release
Nesta fase, a aplicação já foi testada e está pronta para ser disponibilizada aos usuários.

✔ Automação do Deploy → A entrega pode ser totalmente automatizada ou sob aprovação manual.
✔ Gerenciamento de Versões → Mantém controle de versões e possibilita rollback em caso de falha.
✔ Estratégias de Deploy → Blue-Green, Canary Release, Rolling Update, entre outras.

🔹 Ferramentas no GCP para Release:

Cloud Deploy → Serviço gerenciado para pipelines de entrega contínua.
Google Kubernetes Engine (GKE) → Atualizações contínuas para contêineres Kubernetes.
Cloud Run → Atualizações automáticas para aplicações serverless baseadas em contêineres.
App Engine → Deploy e rollback automatizados para aplicativos web.
Compute Engine → Scripts automatizados para VMs.

### Monitor
Depois do release, é fundamental monitorar a aplicação para identificar falhas e otimizar o desempenho.

✔ Métricas de desempenho e uso → Tempo de resposta, taxa de erro, latência, etc.
✔ Monitoramento de logs e alertas → Identificação de erros e falhas em tempo real.
✔ Automação de rollback → Caso falhas sejam detectadas, a versão anterior pode ser restaurada automaticamente.

🔹 Ferramentas no GCP para Monitoramento:

Cloud Monitoring → Coleta métricas de VMs, Kubernetes, Cloud Run, App Engine e mais.
Cloud Logging → Centraliza logs de aplicação, banco de dados e infraestrutura.
Cloud Trace → Identifica gargalos de performance e tempo de resposta de APIs.
Cloud Error Reporting → Detecta e agrupa erros automaticamente.
Cloud Profiler → Análise de performance do código em produção.

## Porque usar Containers e Kubernetes?
Os containers e o Kubernetes são amplamente utilizados para modernizar a implantação e a escalabilidade de aplicações. Eles oferecem maior portabilidade, eficiência e automação, tornando a infraestrutura de TI mais resiliente e escalável.

### Containers
Containers são unidades leves e portáteis que empacotam uma aplicação junto com todas as suas dependências (bibliotecas, runtime, configurações) para rodar de maneira consistente em qualquer ambiente.

✔ Portabilidade → Um container pode rodar em qualquer ambiente, desde o laptop de um desenvolvedor até servidores na nuvem.
✔ Consistência → "Funciona na minha máquina" não é mais um problema; o container garante o mesmo comportamento em qualquer lugar.
✔ Eficiência → Containers compartilham o mesmo kernel do sistema operacional, consumindo menos recursos do que máquinas virtuais.
✔ Isolamento → Cada container executa sua própria aplicação separadamente, evitando conflitos entre dependências.
✔ Escalabilidade → Facilita a criação de múltiplas instâncias da aplicação conforme a demanda.

### Kubernetes
O Kubernetes é uma plataforma de orquestração de containers que gerencia a implantação, escalabilidade e operação de aplicações baseadas em containers.

✔ Automação de Deploys e Rollbacks → Permite lançar novas versões automaticamente e reverter em caso de falha.
✔ Balanceamento de Carga → Distribui o tráfego entre várias instâncias da aplicação.
✔ Escalabilidade Automática → Aumenta ou reduz o número de containers com base no uso de CPU e memória.
✔ Gerenciamento de Recursos → Garante o uso eficiente de CPU e memória, alocando recursos conforme necessário.
✔ Alta Disponibilidade → Se um nó do cluster falhar, o Kubernetes redistribui os containers automaticamente.

## Compute Engine, Kubernetes Engine, Cloud Run e Cloud Functions
# Comparação entre Compute Engine, Kubernetes Engine, Cloud Run e Cloud Functions

| Característica         | Compute Engine (VMs)        | Kubernetes Engine (GKE)  | Cloud Run (Serverless Containers) | Cloud Functions (FaaS) |
|------------------------|---------------------------|-------------------------|----------------------------------|------------------------|
| **Modelo de Execução**  | Máquinas Virtuais (VMs)    | Orquestração de Containers | Containers Serverless            | Funções Serverless     |
| **Gerenciamento**       | Totalmente gerenciado pelo usuário | Kubernetes gerenciado pelo usuário | Totalmente gerenciado pelo Google | Totalmente gerenciado pelo Google |
| **Escalabilidade**      | Manual ou Autoscaler       | Automático via Kubernetes | Automático (scale to zero)      | Automático (scale to zero) |
| **Tempo de Inicialização** | Minutos                  | Segundos a minutos       | Milissegundos a segundos        | Milissegundos          |
| **Casos de Uso**        | Aplicações legadas, bancos de dados, workloads personalizados | Aplicações escaláveis baseadas em containers | APIs, microsserviços, aplicações event-driven | Tarefas curtas, event-driven (triggers como Pub/Sub, Cloud Storage) |
| **Custo**              | Paga pelo tempo da VM ativa | Paga pelos nós e recursos alocados | Paga somente pelo uso (segundos de execução) | Paga apenas pelo tempo de execução da função |
| **Flexibilidade**      | Total controle do SO e configuração | Controle dos containers e rede | Menos controle, mas simplificado | Sem controle sobre infraestrutura |
| **Rede**              | Configuração manual | Integração com redes e balanceamento de carga | HTTP/HTTPS, suporte a VPC | HTTP/HTTPS, Pub/Sub, Cloud Storage triggers |
| **Atualizações e Deploys** | Manuais ou via scripts | Gerenciados via Kubernetes | Automatizados e rápidos | Automatizados |
| **Persistência de Estado** | Sim (Discos Persistentes) | Sim (Discos em nós Kubernetes) | Não (stateless) | Não (stateless) |


## App Engine
É uma plataforma serverless gerenciada no Google Cloud que permite desenvolver, implantar e escalar aplicações web sem precisar gerenciar infraestrutura. Ele suporta diversas linguagens e frameworks populares, automatizando escalabilidade, segurança e balanceamento de carga.

Infraestrutura Gerenciada → O Google cuida dos servidores, rede, segurança e escalabilidade.
✔ Escalabilidade Automática → Aumenta ou reduz recursos de acordo com a demanda (escala até zero).
✔ Suporte a Várias Linguagens → Nativamente suporta Python, Java, Node.js, Go, PHP, Ruby e .NET.
✔ Fácil Deploy → Apenas um comando para implantar aplicações.
✔ Banco de Dados Integrado → Suporte ao Cloud Datastore, Firestore e Cloud SQL.
✔ Segurança → Atualizações automáticas de patches e integração com IAM e Identity-Aware Proxy (IAP).
✔ Dois Ambientes Disponíveis → Standard Environment (serverless total) e Flexible Environment (maior controle).

### Modelos de Execução do App Engine
#### Standard Environment (Ambiente Padrão)
Ideal para aplicações leves e altamente escaláveis.

✔ Tempo de inicialização rápido (milissegundos a segundos).
✔ Suporte a linguagens com runtime gerenciado.
✔ Escala automaticamente até zero (sem cobrança se não estiver em uso).
✔ Restrições de runtime e configurações fixas.

🔹 Casos de Uso:

Aplicações web de alta demanda.
APIs de backend que precisam de resposta rápida.
Microsserviços sem necessidade de persistência no sistema de arquivos.

#### Flexible Environment (Ambiente Flexível)
Para aplicações mais robustas que precisam de mais controle.

✔ Suporte a qualquer linguagem usando containers Docker.
✔ Execução em máquinas virtuais gerenciadas.
✔ Acesso a rede e configurações personalizadas.
✔ Tempo de inicialização mais alto (segundos a minutos).

🔹 Casos de Uso:

Aplicações que exigem bibliotecas personalizadas ou runtime próprio.
Processamento de dados contínuo.
Aplicações que precisam de acesso a recursos do sistema operacional.

## Monitoramento
| Serviço              | O que faz?                                      | Melhor para...                                  | Tipo de Dados Coletados       | Integração com Alertas |
|----------------------|--------------------------------|--------------------------------|-----------------------------|----------------------|
| **Cloud Logging**   | Armazena e analisa logs de aplicações, sistemas e infraestrutura. | Monitoramento de logs e auditoria. | Logs de eventos, erros e auditoria. | Sim (com Cloud Monitoring) |
| **Cloud Trace**     | Analisa latência e desempenho de aplicações distribuídas. | Identificar gargalos de performance. | Tempo de execução de requisições e dependências. | Sim |
| **Cloud Monitoring** | Coleta e exibe métricas de desempenho de serviços e infraestrutura. | Monitoramento em tempo real e geração de alertas. | Uso de CPU, memória, latência, uptime. | Sim |
| **Error Reporting** | Detecta, agrupa e alerta sobre erros de aplicações automaticamente. | Diagnóstico de falhas e estabilidade do sistema. | Stack traces de exceções e falhas. | Sim |
| **Cloud Profiler**  | Analisa o consumo de CPU e memória de aplicações em produção. | Otimização de código e redução de custos computacionais. | Dados de CPU, memória e tempo de execução. | Não |

- **Cloud Logging** → Melhor para **registro e auditoria de eventos e logs** de sistemas e aplicações.  
- **Cloud Trace** → Ideal para **identificar gargalos de latência** em aplicações distribuídas.  
- **Cloud Monitoring** → Essencial para **acompanhar métricas de performance** e ativar **alertas automáticos**.  
- **Error Reporting** → Ajuda na **identificação e rastreamento de erros** de aplicações.  
- **Cloud Profiler** → Ferramenta avançada para **analisar e otimizar desempenho** da aplicação.  

## SLI e SLO
O **Service Level Indicator (SLI)** é uma **métrica quantitativa** que mede a **qualidade e desempenho de um serviço**. Ele representa o nível real de um serviço com base em parâmetros como:

✔ **Disponibilidade** → Percentual de tempo que um serviço está funcionando corretamente.  
✔ **Latência** → Tempo de resposta médio ou percentual de requisições abaixo de um limite.  
✔ **Taxa de erro** → Percentual de requisições bem-sucedidas versus falhas.  
✔ **Vazão (Throughput)** → Número de requisições processadas por segundo.  

🔹 **Exemplo de SLI:**  
- "O serviço respondeu com sucesso em **99,95% das requisições nos últimos 30 dias**."
- "A latência média das requisições foi inferior a **200ms** em 95% dos casos."

## O que é SLO (Service Level Objective)?
O **Service Level Objective (SLO)** é o **objetivo que a equipe define** para um SLI, servindo como **meta de desempenho** do serviço. Ele ajuda a garantir que um serviço **atenda às expectativas** de qualidade e confiabilidade.

✔ **SLOs são usados para definir SLAs (Service Level Agreements)**.  
✔ **Define um alvo que deve ser monitorado continuamente**.  
✔ **Ajuda a tomar decisões sobre escalabilidade e otimização de recursos**.  

**Exemplo de SLO:**  
- "Nosso objetivo é garantir que **99,9% das requisições sejam processadas com sucesso**."
- "A latência média deve ser **inferior a 150ms em 99% das requisições**."

---

#### Como Usar SLI e SLO no GCP?
No Google Cloud, podemos definir e monitorar **SLIs e SLOs** usando o **Cloud Monitoring**.  

### **Passos para Configuração no GCP:**
1 - **Definir um SLI** → Escolher a métrica que representa a qualidade do serviço.  
2 - **Estabelecer um SLO** → Definir a meta de desempenho esperada.  
3 - **Monitorar no Cloud Monitoring** → Criar dashboards e alertas.  
4 - **Gerar relatórios e tomar ações** → Identificar falhas e ajustar a infraestrutura.  