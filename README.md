**Seja bem vindo a este novo repo que desenvolvi :)**

Este repo tem como objetivo apresentar conceitos que a AWS prove para nós profissionais de segurança idenpendentemente se você atua com IAM, Cloudsecurity ou GRC, todo conhecimento é valido e neste repositório trago a seguinte composição.

**Conceito do IAM;**

O AWS IAM (Identity and Access Management) é um serviço da Amazon Web Services (AWS) que permite gerenciar o acesso aos recursos da AWS de maneira segura. Ele ajuda a controlar quem pode fazer o quê dentro de uma conta AWS, garantindo que os usuários e sistemas tenham apenas as permissões necessárias para realizar suas tarefas.

**Aqui estão os principais conceitos do AWS IAM:**

**Usuários (Users)**: Representam uma pessoa ou sistema que precisa acessar recursos da AWS. Cada usuário tem suas próprias credenciais (nome de usuário e senha ou chaves de acesso) e pode ter permissões associadas a ele.

**Grupos (Groups)**: São coleções de usuários que podem ser atribuídos a uma ou mais políticas de acesso. Ao adicionar um usuário a um grupo, ele herda as permissões definidas na política do grupo.

**Políticas (Policies):** São conjuntos de permissões que definem o que os usuários, grupos ou funções podem fazer com os recursos da AWS. As políticas podem ser gerenciadas pela AWS (políticas predefinidas) ou personalizadas pelo administrador da conta. As permissões podem incluir ações como "ler", "escrever", "excluir" recursos específicos.

**Funções (Roles):** São identidades do IAM com permissões associadas, mas ao contrário dos usuários, elas não são vinculadas a um único conjunto de credenciais. Funções são geralmente assumidas por usuários ou serviços para executar tarefas específicas. As funções são frequentemente usadas para delegação de permissões, como dar a um serviço da AWS (exemplo: EC2, Lambda) a capacidade de acessar outros recursos.

**Permissões (Permissions):** Controlam as ações que os usuários, grupos ou funções podem realizar sobre os recursos. As permissões podem ser atribuídas diretamente aos usuários ou através de grupos ou funções.

Políticas Baseadas em Função (Managed Policies) e Políticas Inline:

**Políticas gerenciadas:** São políticas predefinidas pela AWS ou personalizadas, que podem ser aplicadas a vários usuários ou funções.

**Políticas Inline:** São políticas vinculadas diretamente a um único usuário, grupo ou função e não podem ser compartilhadas entre diferentes recursos.

**Autenticação Multifatorial (MFA):** Uma camada adicional de segurança para garantir que os usuários forneçam mais de uma prova de identidade ao fazer login, como um código gerado por um dispositivo ou aplicativo.

**Chaves de Acesso (Access Keys):** São usadas para autenticar e autorizar o acesso de aplicativos ou serviços à AWS, permitindo a comunicação programática com os recursos. Normalmente, são usadas para acesso via API.

**Autenticação e Autorização:** O IAM garante que a identidade de quem está solicitando o acesso (autenticação) seja verificada e, em seguida, valida se essa identidade tem permissão para realizar a ação solicitada (autorização).

Políticas de Controle de Acesso Baseadas em Recursos (Resource-Based Policies): São políticas que podem ser associadas diretamente a um recurso específico, como um bucket S3 ou uma fila SQS, e permitem o controle sobre quem pode acessar esse recurso específico.

Segurança de Acesso e Auditoria: O IAM permite o uso de logs de auditoria através do AWS CloudTrail, o que ajuda a monitorar e registrar todas as atividades de acesso e ações realizadas pelos usuários e serviços, contribuindo para a segurança e a conformidade.

Princípios de Mínimos Privilégios: No AWS IAM, a recomendação é conceder o mínimo de permissões necessárias para realizar uma tarefa, o que limita o risco de acessos indevidos.

Esses conceitos formam a base do AWS IAM e são fundamentais para configurar e gerenciar a segurança e o acesso dentro de uma conta AWS, ajudando a proteger recursos valiosos e garantir que apenas os usuários autorizados possam interagir com os sistemas de forma controlada e eficiente.

**O que é o Permission boundary;**

No AWS IAM (Identity and Access Management), uma Permission Boundary (Limite de Permissões) é um recurso que define um limite máximo de permissões que podem ser atribuídas a uma função ou usuário. Ele age como uma camada de segurança adicional, restringindo as permissões concedidas por uma política de IAM, sem impedir o funcionamento das permissões próprias associadas ao usuário ou à função.

**Como funciona?**

O Permission Boundary funciona como uma restrição superior para as permissões atribuídas ao usuário ou à função. Ou seja, ele define um conjunto de permissões máximas que o usuário ou a função pode ter, independentemente das permissões concedidas pelas políticas associadas a ele.

Políticas de permissões normais: Determinam o que o usuário ou função pode fazer (quais ações ele pode executar, em quais recursos).

Permission Boundary: Estabelece um limite superior para essas permissões. Mesmo que uma política conceda permissões mais amplas, o usuário ou a função não poderá realizar ações fora das permissões definidas pelo Boundary.

**Por que usar o Permission Boundary?**
Delegação de acesso: Permite delegar a criação de usuários ou funções a administradores de diferentes departamentos, mantendo um controle centralizado sobre o máximo de permissões que eles podem ter. Por exemplo, um administrador de recursos de TI pode conceder permissões para gerenciar instâncias EC2, mas com o Permission Boundary, ele não poderá conceder permissões para deletar ou alterar configurações críticas, como VPCs ou IAM.

Segurança aprimorada: Ao usar Permission Boundaries, é possível reduzir o risco de um usuário ou função obter permissões excessivas, limitando suas ações a um conjunto controlado de recursos e operações.

Gerenciamento de permissões complexas: Em organizações com múltiplos níveis de administração, o Permission Boundary permite que os administradores defina regras precisas sobre quem pode fazer o quê, mantendo a governança sobre permissões de forma granular.

**Como aplicar na prática;**
No conceito da arquitetura desenvolvida um usuário terá acesso a console AWs por meio do navegador e nesta navegação ele permite que o usuário gerencie as instâncias EC2, crie containers e registre imagens, apenas isso, porém como uma forma de tentar burlar essa permissão apenas ele possui uma concessão de acesso ao IAM com o famoso *, entretanto, ele não conseguirá por possui o conceito do permissions boundary. 
