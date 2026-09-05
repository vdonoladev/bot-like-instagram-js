# ❤️ Instagram Auto-Liker Bot (JS)

Um script leve em JavaScript puro para ser executado diretamente no console de desenvolvedor (DevTools) do navegador, automatizando o ato de curtir publicações em sequência e avançar para o próximo post com um intervalo de tempo seguro.

## 📌 Visão Geral

O script localiza o botão de curtir dentro da publicação aberta, clica nele (caso esteja disponível), incrementa um contador com feedback no console e em seguida aciona a navegação para o próximo post, repetindo o ciclo a cada 10 segundos.

## 🛠️ Tecnologias Utilizadas

- **JavaScript (ES6+)**
- **DOM API** (Execução nativa no navegador)

## 🚀 Como Usar

### 1. Acesse a Publicação no Instagram
1. Abra o [Instagram Web](https://www.instagram.com) no seu navegador.
2. Pesquise por uma hashtag (ex.: `#fotografia`) ou abra o perfil desejado.
3. Clique na primeira publicação para abri-la no modo de visualização ampliada (modal).

### 2. Abra o Console do Desenvolvedor
- Pressione `F12` ou `Ctrl + Shift + I` (no macOS: `Cmd + Option + I`).
- Selecione a aba **Console**.

### 3. Execute o Script
Cole o conteúdo do arquivo `index.js` no console e pressione **Enter**:

```javascript
const next = document.querySelector("a.coreSpriteRightPaginationArrow");
var counter = 0;

function doLike() {
  const like_btn = document.querySelector(
    "article > div.eo2As > section.ltpMr.Slqrh > span.fr66n > button"
  );

  if (like_btn) {
    like_btn.click();
    counter++;
    console.log(`Você curtiu ${counter} post(s)!`);
  }
  next.click();
}

(function loop() {
  setTimeout(() => {
    doLike();
    loop();
  }, 10000); // Intervalo de 10 segundos
})();
```

Para parar o script, basta recarregar a página (`F5`).

## ⚙️ Como Funciona

* **Recursão com Timeout:** A função auto-executável `loop()` utiliza `setTimeout` de 10 segundos (10.000 ms) entre cada ação para simular um comportamento mais cadenciado.
* **Detecção e Clique:** A função `doLike()` procura o seletor do botão de curtir, realiza o clique, atualiza o contador e avança para a próxima publicação via botão de seta (`coreSpriteRightPaginationArrow`).

## ⚠️ Avisos Importantes

1. **Classes CSS Dinâmicas:** O Instagram altera com frequência a estrutura do DOM e os nomes de classes (como `eo2As`, `fr66n`, `coreSpriteRightPaginationArrow`). Se o bot parar de curtir ou avançar, inspecione a página para atualizar os seletores CSS.
2. **Políticas de Rate Limit:** Curtidas automatizadas contínuas podem disparar bloqueios temporários de ação ou restrições na sua conta. Recomenda-se não deixar o script rodando por períodos prolongados.

## 📄 Licença

Distribuído sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para obter mais informações.
