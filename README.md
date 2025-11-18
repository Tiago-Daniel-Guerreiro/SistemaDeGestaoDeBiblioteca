# Sistema de Gestão de Biblioteca
![Language](https://img.shields.io/badge/Python-3.13-blue.svg)
![Status](https://img.shields.io/badge/Status-Projeto%20Escolar-brightgreen)

Um sistema de gestão de biblioteca desenvolvido em Python como parte da disciplina de Programação de Sistemas de Informação. A aplicação permite o cadastro de livros e alunos, a criação de relatórios, o controlo de empréstimos e devoluções. Todos os dados são guardados em ficheiros JSON, garantindo que a informação não se perde entre sessões.
## 🎯 Objetivo Principal
O objetivo central foi criar um sistema funcional para a gestão de uma biblioteca escolar, focando-se na aplicação de conceitos de programação modular e na manipulação de dados. As metas principais incluíam:
- **Gerir o Catálogo:** Permitir o cadastro, remoção e pesquisa de livros.
- **Gerir Utilizadores:** Permitir o cadastro, remoção e pesquisa de alunos.
- **Controlar Empréstimos:** Implementar a lógica para emprestar e devolver livros, associando-os corretamente aos alunos.
- **Persistência de Dados:** Garantir que todos os dados (livros, alunos e empréstimos) sejam guardados ao fechar a aplicação e carregados ao iniciá-la.
- **Geração de Relatórios:** Criar ficheiros de texto (`.txt`) com informações selecionadas sobre o estado da biblioteca.

## ❓ O Problema
A gestão manual de uma biblioteca, mesmo que pequena, é suscetível a erros e ineficiências. É difícil saber rapidamente quais livros estão disponíveis, quem tem um determinado livro emprestado, ou ter uma visão geral do acervo. A falta de um sistema digitalizado torna o controlo de empréstimos e devoluções uma tarefa manual e demorada.

## ✔️ A Solução
Foi desenvolvido um sistema de linha de comando (CLI) com uma arquitetura modular clara, onde cada classe tem uma responsabilidade bem definida:
1.  **Modelo de Dados (`Livro`, `Aluno`):**
    - Classes simples que representam as entidades fundamentais do sistema.
    - O `Livro` controla o seu próprio estado de disponibilidade (`disponivel`).
    - O `Aluno` mantém uma lista dos livros que tem em sua posse.

2.  **Orquestrador Central (`Biblioteca`):**
    - Armazena as listas de todos os livros e alunos.
    - Centraliza a lógica de negócio, como validar se um livro pode ser emprestado ou se um aluno já está registado.

3.  **Persistência de Dados (`Biblioteca_JSON`):**
    - Uma classe dedicada a salvar e carregar o estado completo da classe `Biblioteca`.
    - Utiliza o formato JSON para serializar todos os objetos (livros, alunos e suas relações) num único ficheiro, garantindo a integridade dos dados entre execuções.

4.  **Geração de Relatórios (`Relatorio`):**
    - Responsável por agregar e formatar os dados da biblioteca num formato de texto legível.
    - Permite ao utilizador escolher quais secções (livros, alunos, empréstimos) devem ser incluídas no relatório final.

5.  **Interface de Utilizador (`Console_Biblioteca`):**
    - Implementa um menu interativo no terminal.
    - Guia o utilizador através de opções numeradas para aceder a todas as funcionalidades do sistema, como cadastrar, emprestar, devolver e gerar relatórios.

## 👤 Meu Papel
Este projeto foi desenvolvido em colaboração. Fui o principal responsável por três áreas-chave do sistema:
- **Desenho da Arquitetura de Classes:** Estruturei o modelo de dados, definindo como as classes `Livro`, `Aluno` e `Biblioteca` interagem entre si para representar o estado do sistema de forma coesa.
- **Implementação da Lógica de Negócio Core:** Desenvolvi o sistema de empréstimos e devoluções, implementando as validações necessárias para garantir a integridade dos dados (ex: impedir que um livro já emprestado seja emprestado novamente).
- **Construção da Interface de Utilizador (CLI):** Criei toda a experiência interativa na consola (`Console_Biblioteca`), que serve como o ponto de entrada para que o utilizador possa aceder a todas as funcionalidades do sistema de forma intuitiva.

## ⚙️ Principais Desafios
- **Adaptação da Interface:** O plano inicial era construir uma interface gráfica (GUI) com Tkinter. No entanto, devido a restrições de tempo, foi necessário tomar a decisão pragmática de mudar para uma interface de linha de comando (CLI), o que exigiu a reestruturação da interação com o utilizador.
- **Garantir a Consistência dos Dados:** Implementar as validações necessárias para evitar inconsistências, como impedir o empréstimo de um livro já emprestado ou o registo de um aluno com uma matrícula duplicada.
- **Serialização de Objetos:** Estruturar as classes com métodos `to_dict()` e `from_dict()` para garantir que pudessem ser corretamente salvas e carregadas a partir do ficheiro JSON.

## ✅ Resultados
- **Sistema Funcional:** Um programa completo que cumpre todos os requisitos definidos, permitindo a gestão eficaz de uma pequena biblioteca.
- **Persistência de Dados:** O sistema armazena e recupera com sucesso todo o seu estado, tornando-o uma ferramenta útil e não apenas uma simulação temporária.
- **Código Modular:** A separação de responsabilidades em diferentes classes torna o código mais fácil de entender, manter e expandir no futuro.

## 🔮 Próximos Passos
O projeto atual serve como uma base sólida para várias melhorias futuras:
- **Implementar a Interface Gráfica (GUI):** Retomar a ideia original e desenvolver uma interface visual com Tkinter, PyQt ou outra biblioteca para uma experiência mais amigável.
- **Gestão de Datas:** Adicionar datas de empréstimo e de devolução, permitindo calcular multas ou identificar livros atrasados.
- **Pesquisa Avançada:** Melhorar as funcionalidades de pesquisa para permitir procurar livros por autor ou alunos por parte do nome.
- **Validação de Entrada:** Implementar validações mais robustas para os dados inseridos pelo utilizador (ex: garantir que o código de um livro segue um formato 
