# 🛡️ Resumo do Lab: Governança e Conformidade - Microsoft Azure AZ-900
Este repositório reúne os principais aprendizados adquiridos durante o laboratório de **Governança e Conformidade no Azure** da plataforma [DIO.me](https://web.dio.me), Módulo 3, do qual estou atualmente participando. O foco está nos benefícios e aplicações práticas da plataforma Microsoft Azure, explorando seus recursos e funcionalidades. O Bootcamp oferece uma base sólida em tecnologias de nuvem, abordando desde os conceitos fundamentais até os componentes essenciais da arquitetura Azure.
Entre os temas estudados estão: criação e gerenciamento de máquinas virtuais, configuração de bancos de dados e soluções de armazenamento, além de tópicos avançados como arquitetura em nuvem, governança, monitoramento e segurança de ambientes cloud.

---
## 📘 Tópicos Abordados
 A governança no Azure é um conjunto de ferramentas e serviços que ajudam a gerenciar, controlar e auditar os recursos na nuvem.
 Ela é fundamental para manter a segurança, otimizar custos e garantir a conformidade com as regulamentações internas e externas. A seguir, abordado os principais tópicos.


## 📘 1. Azure Blueprints (Projetos do Azure)
O **Azure Blueprints** é uma maneira de orquestrar e implantar ambientes de nuvem pré-configurados. Ele agrupa um conjunto de padrões, como:

- Políticas
- Atribuições de função
- Modelos ARM (Resource Manager)
- Grupos de recursos

Tudo isso em um único pacote reutilizável.

**Ideal para:** padronizar ambientes (ex: produção, testes) com configurações pré-aprovadas.

**Exemplo:**  Um blueprint pode incluir:
- Uma política que exige criptografia em discos  
- Um grupo de recursos  
- Uma role de acesso

**Para que serve:**  
Garante que as implantações de recursos sigam os padrões de conformidade e governança da sua organização desde o início. Em vez de configurar manualmente cada recurso, você aplica um "projeto" que já inclui todas as regras e configurações necessárias.

**Como funciona:**  
Você define um projeto que, por exemplo, exige que todas as máquinas virtuais em um grupo de recursos tenham:
- Uma tag específica
- Uma política de segurança ativada
- Um bloqueio de recursos

Ao atribuir esse projeto a uma assinatura, o Azure garante que todos os recursos criados atendam a esses requisitos.

## 📜 2. Políticas e Bloqueios de Recursos

### Azure Policy (Política do Azure)

O **Azure Policy** é um serviço que ajuda a impor regras e efeitos sobre os seus recursos para que eles permaneçam em conformidade com os padrões da sua organização.

As políticas podem:
- Auditar recursos existentes
- Negar ou impedir a criação de novos recursos que não atendam às regras

**Para que serve:**  
Permite definir regras de negócios. Exemplos:

- Proibir a criação de máquinas virtuais de um tipo específico  
- Exigir que todos os recursos tenham a tag `departamento`  
- Auditar se as máquinas virtuais estão usando criptografia

**Como funciona:**

- **Definição de Política:** Criação de uma regra que descreve a condição e o efeito (ex: `auditar`, `negar`)
- **Atribuição de Política:** A política é atribuída a um escopo (grupo de gerenciamento, assinatura ou grupo de recursos)
- **Efeitos:**  
  - `Deny`: nega a criação do recurso  
  - `Audit`: apenas reporta a não conformidade  
  - `Append`: adiciona uma tag ou valor  
  - Outros efeitos disponíveis

**Exemplo:** Uma política pode impedir a criação de máquinas virtuais fora da região `Brazil South`.

### 🔒 Bloqueios de Recursos
O **bloqueio de recursos** protege contra exclusão ou modificação acidental. Pode ser aplicado a:

- Recurso individual
- Grupo de recursos
- Assinatura inteira

**Importante:**  Bloqueios são herdáveis. Se aplicados a um `resource group`, todos os recursos dentro dele herdarão o bloqueio.

**Tipos de Bloqueio:**

- `Read-only`: visualização permitida, mas sem modificações ou exclusão
- `Delete` (CanNotDelete): permite leitura e modificação, mas impede exclusão

**Como funciona:**  
Ao aplicar um bloqueio, qualquer operação que viole a regra será negada. Isso é essencial para proteger recursos críticos de produção.


## 🔐 Gerenciamento do Bloqueio dos Recursos
O gerenciamento de bloqueios pode ser feito via:

- Portal do Azure
- PowerShell
- CLI

**Recomendação:**  
Configure o controle de acesso (RBAC) para garantir que apenas usuários autorizados possam adicionar, remover ou editar bloqueios.

> ⚠️ **Importante:**  
> As políticas e os bloqueios de recursos trabalham de forma complementar.  
> Uma política pode exigir que um recurso tenha um bloqueio, enquanto o bloqueio impede que o recurso seja excluído, mesmo que a política não o proíba diretamente.


## ⛩️ Microsoft Trust Center (Portal de Confiança da Microsoft)
O **Portal de Confiança da Microsoft** é uma plataforma online que oferece informações detalhadas sobre:

- Segurança
- Privacidade
- Conformidade
- Transparência

Esses dados cobrem os principais serviços em nuvem da Microsoft, como Azure, Microsoft 365, Dynamics 365 e Power Platform. É uma ferramenta essencial para quem usa ou pretende usar os serviços da Microsoft com responsabilidade e segurança.

## 🎯 Para que Serve o Portal de Confiança?
O objetivo principal é fornecer aos clientes e parceiros acesso às informações necessárias para entender como a Microsoft protege seus dados. Funciona como um hub central de:

- Documentação
- Recursos técnicos
- Ferramentas de conformidade

## 🔖 Principais Tópicos e Seções
O portal é estruturado em torno dos pilares de confiança da Microsoft:

### 🔐 1. Segurança

Explica as práticas e tecnologias utilizadas para proteger:

- Infraestrutura de nuvem
- Dados dos clientes
- Aplicações corporativas

**Inclui:**

- Proteção contra ameaças e ataques cibernéticos  
- Criptografia de dados em trânsito e em repouso  
- Controle de acesso físico e lógico aos data centers

### 🕵️‍♂️ 2. Privacidade

Detalha como a Microsoft trata os dados pessoais dos clientes, com foco em:

- Proteção contra acesso indevido  
- Cumprimento de leis como a **GDPR** (Regulamento Geral de Proteção de Dados da UE)

### 📋 3. Conformidade

Essencial para empresas que precisam atender a regulamentações específicas.

**Inclui:**

- Certificações e atestados (ISO 27001, FedRAMP, SOC, etc.)  
- Conformidade por setor (saúde - HIPAA, finanças, governo)

### 🧾 4. Transparência

A Microsoft compartilha:

- Relatórios sobre solicitações de dados por autoridades  
- Informações sobre interrupções de serviço e desempenho

## 👥 Quem Deve Usar o Portal?
- Profissionais de TI e Segurança  
- Equipes Jurídicas e de Conformidade  
- Líderes de Negócios

## 🔍 Microsoft Purview
O **Microsoft Purview** é uma plataforma integrada para:

- Governança de dados  
- Segurança da informação  
- Conformidade regulatória  
- Gerenciamento de riscos

Reúne diversas soluções para proteger e controlar dados em ambientes:

- Nuvem  
- Locais  
- Híbridos

## 🧰 Funcionalidades do Purview

- **Governança de dados:** Descoberta, catalogação e classificação  
- **Proteção de informações sensíveis:** Rotulagem, criptografia, prevenção contra perda de dados  
- **Conformidade regulatória:** LGPD, GDPR, HIPAA  
- **Gestão de riscos internos:** Monitoramento de comportamento, alertas proativos  
- **Auditoria e eDiscovery:** Investigação forense, preservação legal

## ✅ Por que Usar o Purview?

- Visibilidade total sobre onde estão os dados e quem tem acesso  
- Atendimento às normas de conformidade  
- Redução de riscos de vazamentos acidentais ou maliciosos  
- Padronização de processos e melhoria da qualidade dos dados  
- Investigações avançadas com auditoria premium e integração com o **Microsoft Sentinel**

## 🔐 Gerenciamento de Políticas de Acesso no Azure
O **gerenciamento de políticas de acesso** no Azure é um dos pilares fundamentais da segurança e da governança na nuvem. A plataforma utiliza um modelo robusto de **controle de acesso baseado em funções (RBAC)** para definir quem pode acessar e modificar recursos dentro de uma assinatura.

Além disso, políticas específicas podem ser aplicadas para **controlar a movimentação de assinaturas entre diretórios**, garantindo maior controle organizacional.

## ⚠️ Importante

- Apenas **administradores globais com permissões elevadas** podem editar políticas de assinatura.
- Outros usuários têm acesso apenas para **visualizar** as configurações atuais.

## 📜 Políticas de Assinatura
Essas políticas têm como objetivo controlar e restringir a movimentação de assinaturas entre diretórios do Azure.

**Principais funcionalidades:**

- Impedir que usuários movam assinaturas para fora ou para dentro de um diretório  
- Permitir que administradores configurem exceções para usuários específicos  
- Reforçar a governança e reduzir riscos de segurança

## 📍 Como Gerenciar
Para gerenciar políticas de assinatura no Azure:

1. Acesse o **portal do Azure**
2. Navegue até **Assinaturas**
3. Selecione **Gerenciar Políticas**
4. Edite as configurações conforme necessário
5. Salve as alterações

## ✅ Benefícios
Esse modelo garante que o acesso aos recursos seja:

- Controlado de forma segura  
- Alinhado aos limites organizacionais  
- Compatível com exigências regulatórias

---
## ✅ Conclusão
A **governança e conformidade** no Azure não são apenas práticas recomendadas — são elementos essenciais para garantir que os ambientes em nuvem sejam seguros, eficientes e alinhados às exigências legais e organizacionais. Ao integrar ferramentas como **Azure Policy**, **Blueprints**, **Microsoft Trust Center** e **Microsoft Purview**, as empresas conseguem:

- Proteger seus dados com políticas claras e bloqueios eficazes  
- Atender às normas regulatórias com transparência e responsabilidade  
- Controlar o acesso e a movimentação de recursos com precisão  
- Promover uma cultura de segurança e responsabilidade digital

> Este conteúdo faz parte do projeto **Gerenciando Politicas em Acessos Azure - Laboratório** da plataforma DIO.me.

---
 
### 📚 Recursos Complementares
- [Tutorial oficial para criar e gerenciar VMs Windows](https://learn.microsoft.com/pt-br/azure/virtual-machines/windows/tutorial-manage-vm)
- [SQL do Azure para Iniciantes](https://learn.microsoft.com/pt-br/shows/azure-sql-for-beginners/)
- [Portal Microsoft Azure](https://portal.azure.com/#allservices)
- [Calculadora de Preços Azure](https://azure.microsoft.com/pt-br/pricing/calculator/)
- [Criar e Gerenciar Políticas no Azure](https://learn.microsoft.com/pt-br/azure/governance/policy/tutorials/create-and-manage#create-and-assign-an-initiative-definition)
- [Governança, Risco e Conformidade](https://learn.microsoft.com/pt-br/compliance/assurance/assurance-governance)
- [Microsoft Purview](https://learn.microsoft.com/pt-br/purview/)
- [Introdução ao Portal de Confiança](https://learn.microsoft.com/pt-br/purview/get-started-with-service-trust-portal)
- [Portal de Confiança do Serviço](https://servicetrust.microsoft.com/ViewPage/Brazil)

📎 Link do curso: [Microsoft Azure AZ-900 - DIO.me](https://web.dio.me/track/microsoft-azure-az-900)
