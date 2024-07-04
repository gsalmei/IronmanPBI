Ironman World Championship Until 2019.

Este projeto tem como objetivo criar um dashboard com os resultados do Campionato Mundial de Ironman até o ano de 2019.

Para isso, foram definidas as seguintes perguntas a serem respondidas:
1 - De acordo com o ano, quem foram os vencedores, seus tempos e suas nacionalidades?
2 - Quem são os atletas com maior número de vitórias?
3 - Quais são os países com maior número de vencedores?
4 - De acordo com o ano, quem foram os atletas que formaram o pódio?
5 - Qual foi a evolução, nos últimos 10 anos, do tempo que o atleta vencedor levou para completar a prova?

Design
O design do dashboard foi criado com o Figma, utilizando como referência o próprio site do Ironman, utilizando principalmente as cores vermelho, preto e branco para o fundo dos gráficos.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/a1accdf3-9d07-4bec-ace6-56aabc32cb8d)


Respondendo as perguntas de negócio:
1 - De acordo com o ano, quem foram os vencedores, seus tempos e suas nacionalidades?
Para responder esta pergunta, foram utilizados cards filtrados pelo ano, conforme imagem abaixo.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/840e367a-9a07-42d1-9f5b-2e94a2f7d83a)

2 - Quem são os atletas com maior número de vitórias?
Neste caso, foi utilizado um gráfico de barras laterais clusterizadas pelo gênero.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/20478d89-240f-42a8-bc74-385882f9ffbc)


3 - Quais são os países com maior número de vencedores?
Seguindo a mesma ideia da pergunta anterior, foi utilizado também um gráfico de barras, porém ao invés do nome do atleta, exibimos a sigla do país.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/4f56901a-cac1-4baa-95b2-13c91b42e6c9)


4 - De acordo com o ano, quem foram os atletas que formaram o pódio?
Aqui optou-se por utilizar uma tabela resumindo os dados.
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/7db778f8-1a53-4184-8ce3-258cea4f4978)

5 - Qual foi a evolução, nos últimos 10 anos, do tempo que o atleta vencedor levou para completar a prova?
Para responder essa pergunta, foi preciso seguir alguma etapas, descritas abaixo:
1 - Criar uma tabela com os anos disponíveis da base de dados para criar o eixo X;
2 - Criar uma coluna calculada para ter valores númericos do tempo de término da prova. Esta medida transforma o tempo total em segundos.
  Time Seconds = 
  HOUR(IM[Time])* 3600 + MINUTE(IM[Time]) * 60 + SECOND(IM[Time])
3 - Criar uma medida para transformar o tempo em uma string e utilizar como rótulo de dados no gráfico de linhas.
  Time Formated = 
  VAR TotalSegundos = SUM('IM'[Time Seconds])
  VAR Horas = INT(TotalSegundos / 3600)
  VAR Minutos = INT(MOD(TotalSegundos, 3600) / 60)
  VAR Segundos = MOD(TotalSegundos, 60)
  RETURN
  FORMAT(Horas, "00") & ":" & FORMAT(Minutos, "00") & ":" & FORMAT(Segundos, "00")
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/63692a5d-f7a3-46a1-a811-ef8c76e1e2cb)

Como resultado final, obtemos o dashboard abaixo:
![image](https://github.com/gsalmei/IronmanPBI/assets/134868461/1c8918d0-337b-454e-b271-ea061dbdfa9d)

