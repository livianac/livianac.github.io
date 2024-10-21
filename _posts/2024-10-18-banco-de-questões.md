---
layout: post
---

O projeto consiste na criação de um banco de questões usando plataformas como o DBeaver e o Pycharm, e programado em python.
Ele tem como objetivo permitir que o usuário resolva questões dos mais diversos assuntos, testando seus conhecimentos.

Link para o [Respositório no GitHub](https://github.com/liviavianac/banco_de_questoes.git)

# Detalhes do projeto

- **Usando o DBeaver para criar o banco de dados**

  No DBeaver, foi criado um banco de dados com uma tabela divida em duas colunas: uma para perguntas e outra para respostas. É com essa tabela que o nosso programa entende e compara as respostas dadas pelo usuário e entende se está correto ou não.

Um dos comandos utilizados foi o de _criar tabela_

    CREATE TABLE questoes (
      id SERIAL PRIMARY KEY,
      pergunta TEXT NOT NULL,
      resposta_correta TEXT NOT NULL
    );

É nessa tabela que ficam os dados das questões, nesse caso, as perguntas e respectivas respostas.



- **Usando o PyCharm para rodar o programa**
  
  No PyCharm, nós somos capazes de inserir as nossas respostas para uma pergunta, e os comandos fazem com que o texto inserido seja comparado com o texto da tabela, e imprime mensagens caso a resposta esteja correta, ou seja, a resposta inserida é igual à resposta presente na tabela, ou errada, quando as respostas diferem uma da outra.
  
  Isso pode ser feito por meio do código:

      def main():
      db = Database()
      questoes = [Questao(*q) for q in db.buscar_questoes()]
  
      for questao in questoes:
          acertou = False
          while not acertou:
              resposta = input(f"{questao.pergunta} ")
                if questao.verificar_resposta(resposta):
                    print("Correto! Próxima questão...\n")
                    acertou = True
                else:
                    print("Errado! Tente novamente.\n")
