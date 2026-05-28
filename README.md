[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

# PGATS - CI

## Pré-requisitos

1. Instale o [git](https://git-scm.com)
2. Instale o [nodejs](https://nodejs.org/)
3. Instale o Yarn - `npm install -g yarn`
4. Faça um _Fork_ do projeto
5. Clone o repositório para sua máquina (seu fork)
6. Instale as dependências
   ```shell
   cd pgats-ci
   yarn
   ```
7. Execute os testes de unidade - isso vai gerar um relatório
   ```shell
   yarn run test
   ```
8. Abra o relatório de cobertura de código em `reports/coverage/lcov-report`
9. Execute os testes de mutação com o Stryker
   ```shell
   yarn run test:mutation
   ```
10. Abra o relatório de mutação em `reports/mutation`
11. Instale os navegadores do Playwright
    ```shell
    yarn playwright install
    ```
12. Execute os testes end-to-end com o Playwright
    ```shell
    yarn run e2e
    ```
13. Execute a aplicação com `yarn start`
14. Acesse a aplicação publicada [neste link](https://pgats-ci-example.netlify.app)

---

## Estratégia de CI/CD

O código-fonte deste projeto é hospedado no **GitHub**, porém a execução do pipeline de CI é realizada pelo **GitLab CI/CD** por meio do recurso _CI/CD for external repositories_.

**Fluxo:**
1. O desenvolvedor faz push no repositório do GitHub
2. Um webhook notifica o GitLab
3. O GitLab sincroniza o mirror do repositório e executa o pipeline definido em `.gitlab-ci.yml`
4. Os resultados do pipeline (testes, cobertura, mutação, e2e) ficam disponíveis no GitLab

Essa abordagem permite manter o repositório no GitHub e aproveitar os runners e recursos de pipeline do GitLab.

---

💜⚡️

# pgats-ci
