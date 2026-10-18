# Explorando Práticas de Teste

Neste exercício, vamos explorar práticas de teste em sistemas reais utilizando a ferramenta [TestMiner](https://andrehora.github.io/testminer).

O TestMiner permite visualizar e analisar testes de software em repositórios do GitHub, fornecendo dados sobre como os projetos organizam seus testes, como eles evoluem entre versões e quais bibliotecas de teste são utilizadas.
Explore a ferramenta antes de começar para se familiarizar com seu funcionamento.

Mais detalhes no GitHub da ferramenta: https://github.com/andrehora/testminer.

---

## Passo 1: Selecionar DOIS repositórios

Escolha dois repositórios reais que possuam testes de software.
Abaixo estão alguns links para ajudá-lo a encontrar projetos interessantes:

- Python: https://github.com/topics/python?l=python
- JavaScript: https://github.com/topics/javascript?l=javascript
- TypeScript: https://github.com/topics/typescript?l=typescript
- Java: https://github.com/topics/java?l=java

- Tópicos: [ai](https://andrehora.github.io/testminer/#topic:ai), [llm](https://andrehora.github.io/testminer/#topic:llm), [api](https://andrehora.github.io/testminer/#topic:api), [nodejs](https://andrehora.github.io/testminer/#topic:nodejs), [android](https://andrehora.github.io/testminer/#topic:android)

- Por organização: [Google](https://andrehora.github.io/testminer/#google), [Microsoft](https://andrehora.github.io/testminer/#microsoft), [Apple](https://andrehora.github.io/testminer/#apple), [Facebook](https://andrehora.github.io/testminer/#facebook), [Netflix](https://andrehora.github.io/testminer/#netflix), 
[GitHub](https://andrehora.github.io/testminer/#github), [Apache](https://andrehora.github.io/testminer/#apache), [HuggingFace](https://andrehora.github.io/testminer/#huggingface)

## Passo 2: Explorar os repositórios selecionados

Busque os repositórios escolhidos no [TestMiner](https://andrehora.github.io/testminer) e analise os dados de teste gerados pela ferramenta.

## Passo 3: Explicar as prática de teste

Para cada repositório, escolha uma prática ou dado de teste relevante e explique com suas próprias palavras.

---

## Instruções de entrega

1. Faça um `fork` deste repositório (saiba mais sobre forks [aqui](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)).
2. Responda às questões abaixo diretamente neste arquivo `README.md` do seu fork. Pode adicionar imagens para enriquecer sua explicação.
3. No Moodle, submeta apenas a URL do seu fork.

---

## Respostas

### Repositório 1 

Repositório: `https://github.com/fastapi/fastapi`

URL TestMiner: `https://andrehora.github.io/testminer/#fastapi/fastapi`

Explicação: O TestMiner mostra, na seção "Test Dependencies", as bibliotecas de teste usadas pelo FastAPI via PyPI: `pytest`, `pytest-cov`, `pytest-xdist`, `pytest-timeout`, `pytest-sugar`, `pytest-codspeed`, `playwright`, `coverage` e `dnspython`. Isso revela uma prática interessante: o projeto não se limita a testes unitários simples com `pytest`. Ele usa `pytest-xdist` para rodar os testes em paralelo (reduzindo o tempo total da suíte, que tem 370 testes), `playwright` para testes de ponta a ponta envolvendo navegador, e `pytest-codspeed` para rodar benchmarks de performance como parte da própria suíte de testes (há uma categoria dedicada "Benchmarks" com 13 arquivos). Ou seja, o FastAPI integra testes funcionais, testes de regressão de performance e execução paralela no mesmo pipeline de CI, em vez de tratá-los como processos separados.

### Repositório 2

Repositório: `https://github.com/prisma/prisma`

URL TestMiner: `https://andrehora.github.io/testminer/#prisma/prisma`

Explicação: O Prisma é um monorepo grande (1233 arquivos-fonte) e o TestMiner mostra que os testes estão organizados em várias categorias distintas: Tests (632), Test Helpers (1060), Fixtures (580), E2E (884), Snapshots (32), Benchmarks (47) e Mocks (2). Duas práticas chamam atenção. A primeira é o uso extensivo de "Snapshots" (testes de snapshot): em vez de escrever asserções manuais para estruturas complexas (como o schema introspectado de um banco), o teste compara a saída atual com um snapshot salvo anteriormente, facilitando detectar mudanças inesperadas em saídas grandes. A segunda é a dependência `fast-check` listada em "Test Dependencies", que indica o uso de testes baseados em propriedades (property-based testing): em vez de fixar poucos exemplos de entrada, a biblioteca gera automaticamente muitos casos de teste para validar invariantes do código, aumentando a chance de encontrar casos extremos que um teste manual não cobriria.
