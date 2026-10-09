# Cronômetro de apresentações

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Um cronômetro de uma única página para que cada pessoa se apresente na sua vez em reencontros e eventos semelhantes. Basta abrir `index.html` no navegador: sem instalação, servidor ou conexão com a internet.

## Como usar

1. Abra `index.html` no navegador (Safari / Chrome).
2. Na tela de configurações: carregue um CSV (veja `sample/participants.csv` ou use “Carregar exemplo”), marque a presença de cada pessoa, ordene por qualquer campo, defina título / tempo por pessoa / tratamento / idioma e teste os sons.
3. Clique em “Ir para o cronômetro” (isso também ativa o áudio).
4. Use o cronômetro:

| Ação | Efeito |
|---|---|
| `Espaço` / botão Iniciar | Inicia a próxima pessoa (com aplausos) |
| Clicar em um nome na lista da direita | Inicia essa pessoa; quem vinha antes vai para “Pulados” |
| Clicar em um nome em “Pulados” | Inicia essa pessoa |
| Desmarcar “Presente” em “Pulados” | Após confirmar, marca como ausente e remove da lista (o cronômetro continua) |

Faltando 10 s: um tique por segundo · faltando 3 s: bipes rápidos · 0 s: som de explosão e rótulo “Tempo esgotado!”. No canto superior direito aparece o tempo total decorrido; na coluna da direita, as próximas 10 pessoas.

## Formato CSV

A primeira linha é o cabeçalho. UTF-8 e Shift_JIS são detectados automaticamente. As colunas de nome e tratamento são escolhidas pelo cabeçalho (por ex. `nome`, `tratamento`) e podem ser alteradas nas configurações. Se a célula de tratamento estiver vazia, usa-se o tratamento padrão.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Idiomas

16 idiomas: troque em “Idioma” na tela de configurações (no início usa-se o idioma do navegador e sua escolha é salva). Os textos, o título e o tratamento padrão, os dados de exemplo e a posição do tratamento (antes/depois do nome) acompanham o idioma; o árabe usa layout da direita para a esquerda. As traduções não foram revisadas por falantes nativos: edite `I18N` em `index.html` para corrigi-las. Para adicionar um idioma, inclua entradas em `LANGS`, `I18N` e `SAMPLE_NAMES`.

## Celular

Layouts para celular na vertical e na horizontal. No iPhone, a chave de silencioso desliga o som. Abrir o arquivo pelo app Arquivos é o mais confiável; com o GitHub Pages basta abrir uma URL.

## Estrutura

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` contém tudo: o dicionário de idiomas, um analisador de CSV, a tela de configurações, a síntese de sons com Web Audio (sem arquivos de áudio), a lógica do cronômetro (baseada em carimbos de tempo, sem deriva) e a tela de execução. Configurações e progresso são salvos automaticamente em `localStorage`.

Licença: [MIT](LICENSE)
