[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

# PGATS - CI

## Pré-requisitos

1. Instale o [git](https://git-scm.com)
2. Instale o [nodejs](https://nodejs.org/)
3. Instale o Yarn - `npm install -g yarn`
4. Clone este repositório para sua máquina
5. Instale as dependências
   ```shell
   cd pgats-ci-pipeline-exercise-1-gitlab-CI
   yarn
   ```
6. Execute os testes de unidade
   ```shell
   yarn run test
   ```
7. Execute os testes de mutação com o Stryker
   ```shell
   yarn run test:mutation
   ```
8. Instale os navegadores do Playwright
    ```shell
    yarn playwright install
    ```
9. Execute os testes end-to-end com o Playwright
    ```shell
    yarn run e2e
    ```
10. Execute a aplicação localmente
    ```shell
    yarn start
    ```

---

## Estratégia de CI/CD

O código-fonte deste projeto é hospedado no **GitHub**, porém a execução do pipeline de CI é realizada pelo **GitLab CI/CD** por meio do recurso _CI/CD for external repositories_.

**Fluxo:**
1. O desenvolvedor faz push no repositório do GitHub
2. Um webhook notifica o GitLab
3. O GitLab sincroniza o mirror do repositório e executa o pipeline definido em `.gitlab-ci.yml`
4. Os resultados dos jobs ficam disponíveis no GitLab

Essa abordagem permite manter o repositório no GitHub e aproveitar os runners e recursos de pipeline do GitLab.

---

## Pipeline atual (.gitlab-ci.yml)

O pipeline possui o estágio `test` com os seguintes jobs:

1. `unit_tests`
   - Executa `yarn test`
2. `mutation_tests`
   - Executa `yarn test:mutation`
   - Publica artefatos em `reports/mutation/`
3. `e2e_tests`
   - Executa `yarn playwright install` e `yarn e2e`
   - Publica artefatos em `playwright-report/`, `test-results/` e `results.xml`

Observação: localmente você pode usar `npm test` ou `yarn test`; ambos executam a mesma suíte de testes unitários definida no `package.json`.
