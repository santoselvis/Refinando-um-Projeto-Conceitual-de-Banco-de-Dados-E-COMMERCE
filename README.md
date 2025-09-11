# Refinando-um-Projeto-Conceitual-de-Banco-de-Dados-E-COMMERCE
Este repositório contém a documentação e os artefatos relacionados ao refinamento de um projeto conceitual de banco de dados voltado para uma plataforma de e-commerce. O objetivo principal é transformar requisitos de negócio em um modelo conceitual claro, estruturado e alinhado com as boas práticas de modelagem de dados.

##  Conecte-se comigo 
<i> 

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/elvis-franklin)
[![GitHub](https://img.shields.io/badge/GitHub-0077B5?style=for-the-badge&logo=github&logoColor=white)](https://github.com/santoselvis)
[![Perfil DIO](https://img.shields.io/badge/-Meu%20Perfil%20na%20DIO-0077B5?style=for-the-badge&logo=gitbook&logoColor=white)](https://web.dio.me/users/efasantosaju?tab=skills&page=1)
[![E-mail](https://img.shields.io/badge/-Email-0077B5?style=for-the-badge&logo=microsoft-outlook&logoColor=white)](mailto:efasantosaju@gmail.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-0077B5?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/5579991342224) 
<br />
<br />
[![Status](https://img.shields.io/badge/status-%20concluido-blue)](#)
  

## 📋 Levantamento de Requisitos – E-COMMERCE

---

### 🎯 Objetivo do Sistema
Desenvolver um projeto conceitual de banco de dados para criação de um e-commerce que permita o gerenciamento eficiente de produtos, clientes, pedidos e pagamentos.

---

### 📌 Requisitos Funcionais
1. O sistema deve armazenar informações de clientes, sendo que o os clientes podem ser pessoa fisica e juridica (nome, e-mail, CPF/CNPJ, endereço e etc...).
2. O sistema deve cadastrar produtos com nome, descrição, preço e quantidade em estoque.
3. Cada pedido deve estar associado a um cliente.
4. Cada pedido pode conter um ou mais produtos.
5. O sistema deve registrar o status de cada pedido (em processamento, enviado, entregue, cancelado).
6. O sistema deve registrar pagamentos com forma de pagamento e data.



### 📌 Regras de Negócio
- Um cliente pode fazer múltiplos pedidos.
- Um produto pode estar em vários pedidos.
- Um pedido pode conter múltiplos produtos (relação muitos-para-muitos).
- O estoque do produto deve ser atualizado após cada pedido concluído.
- Os produtos podem ser vendidos por terceiros.
- O pagamento deve estar associado a um pedido.
- Entrega – Possui status e código de rastreio.

---

## 🗂️ Modelo Conceitual – E-COMMERCE
Abaixo está a representação do modelo conceitual usando a notação Entidade-Relacionamento (ER) com base nos requisitos levantados.



### 📌 Entidades e Atributos
***Cliente***
- id_cliente (PK)
- nome
- email
- cpf
- endereco


*Produto*
- id_produto (PK)
- nome
- descricao
- preco
- estoque



*Pedido*
- id_pedido (PK)
- id_cliente (FK)
- data_pedido
- status



*Pagamento*
- id_pagamento (PK)
- id_pedido (FK)
- forma_pagamento
- data_pagamento



*Item_Pedido (Entidade Associativa)*
- id_pedido (FK)
- id_produto (FK)
- quantidade
- preco_unitario

---

### 📌 Relacionamentos
- **Cliente 1:N Pedido** – Um cliente pode fazer vários pedidos.
- **Pedido 1:1 Pagamento** – Cada pedido possui um pagamento associado.
- **Pedido N:M Produto** – Representado pela entidade associativa `Item_Pedido`.



# 🔄 Refinamentos do Modelo Conceitual
Este arquivo documenta os ajustes e melhorias feitos após a construção inicial do modelo.



## ✅ Refinamento 1 – Criação da entidade associativa `Item_Pedido`
- **Motivação**: A relação muitos-para-muitos entre Pedido e Produto precisava ser melhor representada.
- **Solução**: Criamos a entidade associativa `Item_Pedido`, permitindo registrar quantidade e preço por item no pedido.



## ✅ Refinamento 2 – Adição de status ao Pedido
- **Motivação**: Era necessário acompanhar o ciclo de vida de um pedido.
- **Solução**: Adicionado o atributo `status` na entidade Pedido (em processamento, enviado, entregue, cancelado).--



## ✅ Refinamento 3 – Registro da forma de pagamento
- **Motivação**: Era importante diferenciar pagamentos (cartão, boleto, pix etc.).
- **Solução**: Adicionado o atributo `forma_pagamento` na entidade Pagamento.



Outros refinamentos poderão ser realizados conforme novos requisitos forem identificados.

# 📌 Caso de Uso: Compra de um Produto

## 🧾 Cenário
O cliente João realiza uma compra de 2 unidades do produto "Fone Bluetooth".



## 📦 Entidades Envolvidas

- **Cliente**: João da Silva (id_cliente = 1)
- **Produto**: Fone Bluetooth (id_produto = 10)
- **Pedido**: id_pedido = 101
- **Item_Pedido**: produto 10, quantidade = 2, preco_unitario = R$ 199,90
- **Pagamento**: forma_pagamento = "Cartão de Crédito", data_pagamento = 10/09/2025



## 🔁 Fluxo Resumido
1. João é cadastrado como cliente.
2. João adiciona 2 fones Bluetooth ao carrinho.
3. Um pedido é criado e associado a João.
4. A entidade `Item_Pedido` é preenchida com os detalhes da compra.
5. O pagamento é registrado e associado ao pedido.
6. O estoque do produto é reduzido em 2 unidades.



> Este é apenas um exemplo para ilustrar como o modelo pode ser utilizado em situações reais.



