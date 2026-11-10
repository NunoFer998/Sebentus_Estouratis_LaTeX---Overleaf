# Sebentus Estouratis: versão LaTeX

Cancioneiro da Tuna de Engenharia da Universidade do Porto, convertido do Word.

## Compilar

**O compilador tem de ser XeLaTeX.** As fontes estão na pasta `fontes/`.

- **MiKTeX (local):** abre `main.tex` no TeXworks ou no TeXstudio e compila. A primeira
  linha (`% !TEX program = xelatex`) já escolhe o XeLaTeX. Na linha de comandos:
  `latexmk main.tex`. Na primeira compilação o MiKTeX pode pedir para instalar
  pacotes em falta; aceita.
- **Overleaf:** *New Project → Upload Project* com o .zip. O ficheiro `latexmkrc`
  já escolhe o XeLaTeX (ou: *Menu → Compiler → XeLaTeX*).
- **Papeeria:** carrega o .zip. Usa XeLaTeX por omissão.
- **Outros:** escolhe XeLaTeX nas definições do projeto.

O índice precisa de duas compilações para ficar certo. O `latexmk` e o Overleaf
fazem isso sozinhos.

## Estrutura

| Ficheiro | Para quê |
|---|---|
| `main.tex` | Ordem das músicas (uma linha `\input{...}` por música) |
| `musicas/*.tex` | Uma música por ficheiro |
| `tuna.sty` | Aspeto do cancioneiro (fontes, margens, cores) |
| `fontes/` | Fontes livres (licença SIL OFL) |

Como cada música está no seu ficheiro, várias pessoas podem editar ao mesmo tempo
sem se atrapalharem.

## Escrever uma música

```latex
\begin{musica}{Engenharia}{Paulino Gomes Júnior}{Tuna de Engenharia da Universidade do Porto}
\nota{Introdução: D E Am}

Engenha\ac{Am}{ria},
Curso que me envai\ac{E}{de}ce
Chama imensa que engran\ac{Am}{de}ce. \ac{A7}{}__

\nota{Refrão:}
É grande \ac{F#m}{luz} d’acade\ac{Bm}{mia} \nota{2x}

\posicoes{D: xx0232, Dm: x00231, E: 022100, F#m: 244222}
\end{musica}
```

- `\begin{musica}{Título}{Original}{Adaptação}`: se não houver adaptação, deixa `{}`.
- **Cada linha do ficheiro é uma linha do cancioneiro.** Uma linha em branco
  separa estrofes.
- `\ac{Am}{ria}`: acorde por cima da sílaba, que fica sublinhada.
  `\ac{A7}{}` põe o acorde nesse ponto, sem sílaba. Se dois acordes ficarem
  demasiado juntos, o LaTeX afasta a letra sozinho.
- `\nota{...}`: texto a vermelho (Refrão, Introdução, 2x, …).
- `\posicoes{...}`: lista de posições no canto inferior direito da página onde a
  música acaba, separadas por vírgulas.
- `#` e `_` escrevem-se diretamente (`F#m`, `__`). Para `%`, `&` e `$` usa
  `\%`, `\&` e `\$`.
- Duas colunas: `\begin{multicols}{2}` … `\end{multicols}`.
- Tablaturas: `\begin{tablatura}` … `\end{tablatura}`. As linhas ficam
  exatamente como estão escritas. Uma linha de acordes por cima da tablatura
  escreve-se com `\acordestab{   Am      E}`.

**Acrescentar uma música:** copia um ficheiro de `musicas/`, muda-lhe o nome e o
conteúdo, e junta `\input{musicas/novo-nome}` no `main.tex`, no sítio onde a
queres.

## Diferenças em relação ao Word

- Fontes livres parecidas: Fira Sans em vez de Trebuchet MS, Liberation em vez de
  Times/Courier, UnifrakturMaguntia em vez de Old English. Num computador com o
  Office podes usar as originais com `\usepackage[fontesword]{tuna}` no `main.tex`.
- A primeira página (em branco no Word) tem agora um índice com ligações, e as
  páginas têm número. Para tirar o índice, apaga `\indice` no `main.tex`.
- O cabeçalho é igual em todas as páginas. No Word alternava entre negrito e
  normal.
- Os acordes ficam exatamente sobre a sílaba sublinhada. No Word estavam por vezes
  uma letra ao lado.
- As quebras de página são automáticas. Cada música começa numa página nova e
  cada tablatura fica inteira na mesma página.
