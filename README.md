```# Na Era do Gelo

Este é um projeto de desenvolvimento de um site para a lanchonete "Na Era do Gelo" usando HTML, Tailwind CSS e JavaScript. O objetivo deste projeto é criar um site responsivo e interativo com design moderno.

## Demonstração

Confira a demonstração ao vivo do site:
[Veja a Demonstração](https://cardapio-naeradogelo.vercel.app)

## Tecnologias Utilizadas

- **HTML**: Linguagem de marcação utilizada para estruturar o conteúdo do site.
- **Tailwind CSS**: Framework CSS para estilização rápida e eficiente.
- **JavaScript**: Linguagem de programação usada para adicionar interatividade ao site.

## Estrutura do Projeto```

A estrutura de diretórios do projeto é a seguinte:

CardapioNaeradogelo/
├── assets/
│ ├── bg.png
│ ├── hamb-1.png
│ ├── hamb-2.png
│ ├── hamb-3.png
│ ├── hamb-4.png
│ ├── logo.png
│ ├── refri-1.png
│ └── refri-2.png
├── styles/
│ └── output.css
├── src/
│ └── script.js
├── index.html
├── tailwind.config.js
└── README.md


## Instalação
'''
Siga os passos abaixo para configurar o projeto localmente:

1. Clone o repositório:
    ```sh
    git clone https://github.com/HiCoderpro/CardapioNaeradogelo.git
    ```

2. Navegue até o diretório do projeto:
    ```sh
    cd CardapioNaeradogelo
    ```

3. Instale as dependências do Tailwind CSS:
    ```sh
    npm install
    ```

4. Gere o arquivo CSS a partir do Tailwind:
    ```sh
    npx tailwindcss -i ./styles/input.css -o ./styles/output.css --watch
    ```
'''
5. Abra o arquivo `index.html` no seu navegador para ver o site.

## Uso

1. **Página Inicial**: Contém o cabeçalho com o logotipo e informações sobre a lanchonete.
2. **Menu**: Exibe os produtos disponíveis, incluindo hambúrgueres e bebidas, com opção de adicionar ao carrinho.
3. **Carrinho**: Modal que mostra os itens adicionados ao carrinho, total da compra e campo para inserir o endereço de entrega.

## Configuração do Tailwind CSS

O arquivo `tailwind.config.js` está configurado da seguinte forma:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./**/*.{html,js}"],
  theme: {
    fontFamily: {
      'sans': ['Poppins', 'sans-serif']
    },
    extend: {
      backgroundImage: {
        "home": "url('/assets/bg.png')"
      }
    },
  },
  plugins: [],
}

Funcionalidades do JavaScript

O arquivo src/script.js é responsável por adicionar interatividade ao site, especialmente para o carrinho de compras. Aqui está uma visão geral das funcionalidades implementadas:

document.addEventListener("DOMContentLoaded", () => {
  const cartBtn = document.getElementById("cart-btn");
  const cartModal = document.getElementById("cart-modal");
  const closeModalBtn = document.getElementById("close-modal-btn");
  const checkoutBtn = document.getElementById("checkout-btn");
  const cartItemsContainer = document.getElementById("cart-items");
  const cartTotal = document.getElementById("cart-total");
  const cartCount = document.getElementById("cart-count");
  const addressInput = document.getElementById("address");
  const addressWarn = document.getElementById("address-warn");

  let cart = [];

  document.querySelectorAll(".add-to-cart-btn").forEach(button => {
    button.addEventListener("click", () => {
      const name = button.getAttribute("data-name");
      const price = parseFloat(button.getAttribute("data-price"));
      const item = cart.find(i => i.name === name);

      if (item) {
        item.quantity++;
      } else {
        cart.push({ name, price, quantity: 1 });
      }

      updateCart();
      showToast(`Adicionado ${name} ao carrinho!`);
    });
  });

  cartBtn.addEventListener("click", () => {
    cartModal.classList.remove("hidden");
  });

  closeModalBtn.addEventListener("click", () => {
    cartModal.classList.add("hidden");
  });

  checkoutBtn.addEventListener("click", () => {
    if (addressInput.value.trim() === "") {
      addressWarn.classList.remove("hidden");
    } else {
      addressWarn.classList.add("hidden");
      // Lógica para finalizar o pedido
      alert("Pedido finalizado com sucesso!");
      cart = [];
      updateCart();
      cartModal.classList.add("hidden");
    }
  });

  function updateCart() {
    cartItemsContainer.innerHTML = "";
    cart.forEach(item => {
      const div = document.createElement("div");
      div.classList.add("flex", "justify-between", "mb-2");
      div.innerHTML = `
        <p>${item.name} x${item.quantity}</p>
        <p>R$${(item.price * item.quantity).toFixed(2)}</p>
      `;
      cartItemsContainer.appendChild(div);
    });

    cartTotal.textContent = cart.reduce((total, item) => total + item.price * item.quantity, 0).toFixed(2);
    cartCount.textContent = cart.length;
  }

  function showToast(message) {
    Toastify({
      text: message,
      duration: 3000,
      close: true,
      gravity: "top",
      position: "right",
      backgroundColor: "linear-gradient(to right, #00b09b, #96c93d)",
    }).showToast();
  }
});


Contribuição

Se você deseja contribuir para este projeto, siga os passos abaixo:

   1 Faça um fork do projeto
   2 Crie uma nova branch:

    git checkout -b minha-nova-feature

 3 Faça suas alterações e commite:
 
 git commit -m 'Adicionei uma nova feature'

 4 Envie para o branch original:
 git push origin minha-nova-feature

Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo LICENSE para mais detalhes.
Contato

Se você tiver alguma dúvida ou sugestão, sinta-se à vontade para entrar em contato:

    Email: lucasemfloripa@gmail.com
    GitHub: HiCoderpro

    

