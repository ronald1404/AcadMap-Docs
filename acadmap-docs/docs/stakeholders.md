# 2. Stakeholders

Stakeholders são indivíduos, grupos ou entidades que possuem interesse direto ou indireto na definição, evolução ou operação do sistema. Identificar claramente esses stakeholders é fundamental para garantir que suas preocupações sejam devidamente consideradas durante a elaboração da arquitetura. Isso contribui para a alocação adequada de responsabilidades, melhora a comunicação entre as partes envolvidas e fortalece o alinhamento entre os objetivos de negócio e as decisões técnicas.

A tabela a seguir apresenta os stakeholders identificados para este projeto, descrevendo seus papéis, responsabilidades e as preocupações arquiteturais que representam.

| ID   | Nome                | Papel                       | Responsabilidades Principais                                      | Preocupações Relacionadas |
| ---- | ------------------- | --------------------------- | ----------------------------------------------------------------- | ------------------------- |
| ST01 | Desenvolvedor Back  | Desenvolvimento do backend  | Implementar lógica de negócio, integrações, persistência          | P01, P06, P07, P09        |
| ST02 | Desenvolvedor Front | Desenvolvimento do frontend | Criar interfaces, garantir UX, consumir APIs                      | P01, P02, P09             |
| ST03 | DPO (Encarregado)   | Conformidade com a LGPD     | Garantir proteção de dados e conformidade com legislações         | P08, P10                  |
| ST04 | Product Owner       | Representante do negócio    | Definir backlog, validar valor para o usuário, priorizar entregas | P02, P04, P08             |
| ST05 | Analista de QA      | Garantia da Qualidade       | Verificar cobertura de testes, detectar falhas, validar entregas  | P03, P06, P09             |

---
