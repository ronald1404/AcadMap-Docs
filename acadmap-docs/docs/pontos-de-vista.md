# 4. Pontos de Vista Arquiteturais

![Static Badge](https://img.shields.io/badge/Arquitetura-%230074B6?style=for-the-badge&logo=githubactions&logoColor=%23F2F2F2)

Pontos de vista arquiteturais são descrições específicas de aspectos do sistema sob diferentes perspectivas, com o objetivo de abordar um subconjunto das preocupações levantadas pelos stakeholders. Cada ponto de vista adota uma notação e uma forma de representação adequada à natureza das informações que transmite. A adoção de múltiplos pontos de vista facilita a comunicação entre as partes interessadas, permite avaliações segmentadas da arquitetura e aumenta a rastreabilidade das decisões técnicas.

A tabela a seguir descreve os pontos de vista adotados neste projeto, sua finalidade, artefatos utilizados e as principais preocupações que cada um trata.

| ID   | Ponto de Vista  | Objetivo                                                       | Notação / Artefato Utilizado             | Preocupações Tratadas        |
| ---- | --------------- | -------------------------------------------------------------- | ---------------------------------------- | ---------------------------- |
| PV01 | Lógico          | Modelar os módulos, componentes e suas responsabilidades       | Diagrama de Componentes (UML)       | P02, P05, P06, P07, P08, P10 |
| PV02 | Desenvolvimento | Representar a organização do código e boas práticas adotadas   | Diagrama de pacotes (UML), árvore de arquivos | P01, P03, P04, P06, P09      |
| PV03 | Implantação     | Modelar a infraestrutura de execução e distribuição do sistema | Diagrama de Deploy (UML)            | P05, P07, P10                |
| PV04 | Processo        | Representar interações e fluxos de execução                    | Diagrama de Sequência (UML)         | P03, P04, P10                |
| PV05 | Uso             | Ilustrar a experiência do usuário e seus fluxos de interação   | Cenários, fluxos, protótipos (Figma)     | P02, P04, P08                |

---
