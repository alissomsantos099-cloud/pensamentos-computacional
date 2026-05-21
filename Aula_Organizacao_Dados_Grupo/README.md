# 🗃️ Organização de Dados: Do Caos à Estrutura
> Atividade Prática: Estruturando Dados - Pensamento Computacional.

![Status](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen?style=for-the-badge)
![UDF](https://img.shields.io/badge/Institui%C3%A7%C3%A3o-UDF-blue?style=for-the-badge)
![Contexto](https://img.shields.io/badge/Projeto-PAI-11caa0?style=for-the-badge)

## 📌 Sobre a Atividade
Este repositório contém a entrega da atividade "Do caos à organização", orientada pela Professora Kadidja Valéria. Como aprendemos na disciplina, "informação bruta não tem utilidade sem arquitetura". 

O objetivo desta etapa é aplicar a teoria computacional para transformar os dados do **Portal Acadêmico Integrado (PAI)** o sistema de larga escala que estamos desenvolvendo ao longo do semestre em conhecimento estruturado.

Para isso, pegamos um conjunto de dados específico do nosso sistema (As Entidades de Usuários, Disciplinas e Motor de IA) e o representamos de três formas computacionais distintas:

### 1. [Lista](./Lista.md) 
* **Foco:** Ordem e Sequência.
* **Aplicação no PAI:** Uma lista linear do fluxo de processamento de notas no sistema, do lançamento pelo professor até a análise de recomendação feita pela inteligência artificial.

### 2. [Grafo](./Grafo.png)
* **Foco:** Conexões e Relacionamentos.
* **Aplicação no PAI:** Uma rede de interações mostrando como as entidades se conectam na prática (ex: Professor leciona para -> Disciplina -> que tem múltiplos -> Alunos).

### 3. [Hierarquia](./Hierarquia.png)
* **Foco:** Níveis e Categorias.
* **Aplicação no PAI:** Um organograma da estrutura de herança e permissões de acesso do sistema (A superclasse `Usuario` subordinando as classes `Aluno` e `Professor`).

---

## 📚 Fundamentação Teórica
A base conceitual para a montagem dessas representações visuais foi extraída da bibliografia da disciplina:
> SANTOS, Marcelo da Silva dos; VOGEL, Adriano José (rev. técnica). *Pensamento Computacional*. Porto Alegre: SAGAH, 2021.

---
**Nome:** ALisson D S Ferreira

