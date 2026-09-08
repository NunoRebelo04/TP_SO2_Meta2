Trabalho Prático - Sistemas Operativos 2
Ano letivo: 2025/2026

M2 - Programa Central e Interação com o Programa Placar

Aluno:
Nuno Guilherme Sampaio Rebelo - 2022137005


Funcionalidades implementadas:

1. Programa Central
- Receção do nome do named pipe através da linha de comandos
- Criação do name pipe no formato "\\.\pipe\<nome>"
- Suporte para múltiplos placares ligados em simultâneo

2. Comunicação via named pipes
- Comunicação bidirecional em modo message
- Criação de uma instância de pipe por placar
- Envio e receção das estruturas:
	- MSG_CMD
	- MSG_ALERTA
	- MSG_ID

3. Gestão de placares
- Receção do pedido "ligar" (MSG_CMD tipo = 1)
- Atribuição automática de identificadores únicos
- Manutenção da lista de placares ligados
- Receção do pedido "desligar" (MSG_CMD tipo = 2)
- Remoção do placar da plataforma

4. Comando "alerta"
- Envio de MSG_ALERTA para um placar específico
- Suporte para envio global (id = 0)
- Receção da confirmação do placar
- Atualização do estado do alerta ativo

5. Comando "cancelar"
- Envio de MSG_CMD (tipo = 5)
- Receção da confirmação do placar
- Remoção do alerta ativo do placar

6. Comando "listar"
- Apresentação dos placares ligados
- Apresentação do alerta ativo de cada placar
- Indicação de placares sem alertas ativos

7. Comando "encerrar"
- Envio de MSG_CMD (tipo = 6) para todos os placares
- Encerramento controlado da plataforma

8. Alterações ao programa Placar
- Envio do pedido "ligar" ao central
- Receção do identificador atribuído
- Envio do pedido "desligar"
- Receção da confirmação do central
- Envio de MSG_CMD (tipo = 3) após terminar a duração do alerta
- Receção de MSG_ALERTA (tipo = 4)
- Confirmação da receção do alerta
- Receção de MSG_CMD (tipo = 5) para cancelamento
- Confirmação do cancelamento
- Receção de MSG_CMD (tipo = 6) para encerramento da plataforma

9. Gestão de alertas
- Apenas um alerta ativo por placar
- Substituição automática do alerta anterior
- Temporização dos alertas com waitable timer
- Apresentação da mensagem "---" após o fim do alerta

10. Concorrência e sincronização
- Utilização de múltiplas threads:
  - interação com utilizador
  - comunicação com placares
  - temporização de alertas
- Utilização de CRITICAL_SECTION para sincronização
- Comunicação assíncrona entre central e placares
