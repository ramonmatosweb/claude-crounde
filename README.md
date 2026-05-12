# 🪟 Janela perfeita do Claude Code

Gerador de cron pra maximizar suas janelas de 5h do Claude Code.

**👉 [Acesse a ferramenta](https://claude-crounde.ramonmatoslima.com.br)**

## O problema

O Claude Code conta uma janela rotativa de 5 horas a partir da sua primeira mensagem do dia. Se você começa a trabalhar às 09h, sua janela acaba às 14h — e a próxima vai até 19h. No expediente padrão (9h-18h), você acessa só **2 janelas**, sendo a segunda incompleta.

## A solução

Mandando uma única mensagem de `ping` **antes do expediente** via cron, você desloca o ciclo de resets pra dentro do horário de trabalho. O resultado:

- Reset acontece **durante** o expediente
- Você acessa até **3 janelas frescas** no mesmo dia
- Cada reset = uma nova cota de uso

A regra: **`warmup = início_do_trabalho − 4h`**.

Pra trabalho 9h-18h, o warmup ideal é **05h00**.

## Como usar

1. Abra https://claude-crounde.ramonmatoslima.com.br
2. Informe seu horário de início e fim do trabalho
3. Copie a linha de cron gerada
4. Cole no seu crontab (`crontab -e`) numa máquina sempre ligada

A máquina precisa ter o `claude` CLI instalado e autenticado.

## Tradeoffs honestos

- ⚠️ O **limite semanal continua valendo**. Warmup não dá mais cota total, só desloca quando os resets acontecem.
- Cada warmup consome ~1 request do plano. Desprezível.
- Funciona melhor pra trabalho ≥ 6h. Pra jornadas curtas (≤5h), uma janela já cobre tudo.
- Você precisa de uma máquina sempre ligada (server, mini PC, VPS) com `claude` CLI instalado.

## Stack

HTML + CSS + JS puro. Zero dependências, zero analytics, zero rastreio.

Hospedado no Vercel. Código aberto sob licença MIT.

## Contribuindo

Sugestões e pull requests bem-vindos. O algoritmo é simples — fique à vontade pra propor melhorias na lógica de cálculo ou na UX.

## Autor

[Ramon Matos](https://ramonmatos.com.br) · 2026
