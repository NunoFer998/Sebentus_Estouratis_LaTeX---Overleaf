# Instalação

Para compilar o cancioneiro precisas de XeLaTeX e de `latexmk`. Escolhe **uma** das opções.

## Opção 1: sem instalar nada (Overleaf)

*New Project → Upload Project* com o Sebentus_Template.zip. Compila sozinho em XeLaTeX.

## Opção 2: instalar no teu computador

### Windows

```
winget install MiKTeX.MiKTeX
winget install StrawberryPerl.StrawberryPerl
```

O Perl é preciso para o `latexmk`. Depois, na MiKTeX Console, em
*Settings → General*, escolhe instalar pacotes em falta automaticamente
(*Always*).

### macOS

```
brew install --cask mactex-no-gui
```

### Linux (Debian/Ubuntu)

```
sudo apt install texlive-xetex texlive-latex-extra texlive-lang-portuguese latexmk
```

Se faltar algum pacote, usa `texlive-full`, que é maior mas inclui tudo.

### PATH

Os instaladores acima acrescentam-no sozinhos. Só tens de **fechar e abrir
o terminal** (ou o VS Code) depois de instalar. Para confirmar:

```
xelatex --version
latexmk --version
```

Se algum der "comando não encontrado", o PATH não foi atualizado. No Windows,
reinicia a sessão; no macOS, o caminho é `/Library/TeX/texbin`.

## Compilar

Na pasta do projeto:

```
latexmk main.tex
```

O resultado é `main.pdf`. Para recompilar sempre que guardas um ficheiro:
`latexmk -pvc main.tex`.

## Ver o PDF enquanto escreves

Instala o VS Code e a extensão **LaTeX Workshop**. Abre `main.tex` e guarda
com Ctrl+S: compila e mostra o PDF ao lado. Precisa de uma das instalações
acima (ou do Dev Container).
