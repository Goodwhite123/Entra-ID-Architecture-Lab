# 🛡️ Microsoft Entra ID - Arquitetura de IAM e Delegação de Acessos

## 📝 Descrição do Projeto
Este projeto é um laboratório prático focado em **Identity and Access Management (IAM)** utilizando o Microsoft Entra ID. O objetivo principal foi desenhar e implementar uma arquitetura de identidades segura, aplicando conceitos de **Zero Trust**, **Princípio do Menor Privilégio (PoLP)** e **Gestão Descentralizada**.

A infraestrutura simula um ambiente corporativo com dois departamentos distintos (Recursos Humanos e Tecnologia da Informação), estabelecendo fronteiras claras de administração e controle de acesso a recursos.

## 🎯 Conceitos e Tecnologias Aplicadas
* **Microsoft Entra ID** (antigo Azure AD)
* **RBAC** (Role-Based Access Control)
* **Administrative Units (AUs)** para delegação de administração
* **Security Groups** e Self-Service Group Management
* **Princípio do Menor Privilégio (PoLP)**

---

## 🏗️ Arquitetura e Implementação

O laboratório foi estruturado em três pilares fundamentais de IAM:

### 1. Provisionamento de Identidades e Separação Lógica
Foram criadas contas de usuários baseadas em departamentos para simular um ambiente real de produção:
* **Departamento de RH:** Usuários padrão (`HR01`, `HR02`, `HR03`) e um administrador departamental (`HRAdmin`).

<img width="1153" height="171" alt="Screenshot 2026-10-12 230551" src="https://github.com/user-attachments/assets/55b0f0a8-0a64-4ad9-b2f8-8874da3b3b6d" />

* **Departamento de TI:** Usuários padrão (`IT01`, `IT02`, `IT03`) e um administrador departamental (`ITAdmin`).

<img width="1007" height="173" alt="Screenshot 2026-10-12 230709" src="https://github.com/user-attachments/assets/598f5b9b-d62d-4487-96ee-bb017d9a39d3" />

### 2. Delegação de Privilégios com Administrative Units (AUs)
Para evitar a concessão de privilégios globais (Global Administrator) e respeitar o conceito de Zero Trust, a administração de contas foi segmentada:
* Criação das Administrative Units: `AU-HR-USERS` e `AU-IT-USER`.

<img width="1370" height="121" alt="image" src="https://github.com/user-attachments/assets/620b2f83-8cbd-4e07-89f4-cffee52be42e" />

* **RBAC na Prática:** O usuário `HRAdmin` recebeu a role de *Helpdesk Administrator* com escopo restrito **apenas** à AU de Recursos Humanos. O mesmo foi aplicado ao `ITAdmin` para a AU de TI.
* **Resultado:** Os administradores departamentais conseguem gerenciar o ciclo de vida (ex: reset de senhas) apenas dos usuários do seu próprio setor, limitando o raio de impacto de um possível comprometimento de credencial.

### 3. Controle de Acesso e Gestão Descentralizada de Grupos
Para gerenciar a autorização e o acesso a recursos corporativos, foram estruturados Grupos de Segurança:
* Criação dos grupos `HR-GROUP` e `IT-Group`.
* **Self-Service Group Management:** Os administradores departamentais (`HRAdmin` e `ITAdmin`) foram definidos como **Owners** (proprietários) de seus respectivos grupos.
* **Valor para o Negócio:** O processo de autorização foi descentralizado. O líder de cada departamento tem autonomia para adicionar ou remover membros dos grupos de acesso sem depender da TI Global, agilizando o onboarding de novos colaboradores e garantindo que o acesso a aplicativos (Enterprise Applications) seja gerenciado por quem entende a necessidade da área.

---

## 🚀 Próximos Passos (Evolução da Arquitetura)
Como evolução natural deste ambiente, a arquitetura está preparada para receber:
1. **Integração de Enterprise Applications:** Vinculação de aplicativos SaaS (ex: Sistemas de Folha de Pagamento) aos Security Groups para provisionamento de acesso via SSO.
2. **Microsoft 365 Groups:** Criação de grupos focados em colaboração (Teams, SharePoint, Calendários) operando em paralelo com os grupos de segurança.
3. **Políticas de Conditional Access:** Exigência de MFA (Multi-Factor Authentication) com base no risco do usuário ou localização de rede.

---

## 👨‍💻 Sobre o Autor
**Gabriel Saes de Sousa**  
*Estudante de Cybersecurity focado em Cloud Security e Identity and Access Management (IAM).*
