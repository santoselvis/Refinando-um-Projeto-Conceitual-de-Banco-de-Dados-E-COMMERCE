# Projeto Conceitual de Banco de Dados - E-commerce
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

---
## Sumario
- 1. Levantamento de Requisitos
- 1.1 Requisitos Funcionais
- 1.2 Regras de Negócio
- 1.3 Modelo Conceitual E-commerce
- 1.4 Entidades e Atributos
- 1.5 Relacionamentos
- 2.0 Refinando o Modelo Conceitual
- 2.1 Primeiro Refinamento - Criação da Entidade Associativa "Item_Pedido"
- 2.2 Segundo Refinamento - Adição de Status do Pedido
- 2.3 Terceiro Refinamento - 
- 2.4 Quarto Refinamento - 
- 2.5 Quinto Refinamento - 
- 2.6 Sexto Refinamento - 
- 2.7 Setimo Refinamento -

### 1.0 Levantamento de Requisitos
Todos os requisitos aqui destacados foram levantados com base no modulo Refinando um Projeto Conceitual de Banco de Dados - E-commerce, parte do Bootcamp Randstad Analise de Dados da DIO. O objetivo é desenvolver um projeto conceitual de banco de dados para criação de um e-commerce que permita o gerenciamento eficiente de produtos, clientes, pedidos e pagamentos e etc...
 
### 1.1 Requisitos Funcionais
1. O sistema deve armazenar informações de clientes, sendo que o os clientes podem ser pessoa fisica e juridica (nome, e-mail, CPF/CNPJ, endereço e etc...).
2. Vendedores terceiros cadastrados podem vender seus produtos no sistema.
3. O sistema deve cadastrar produtos com nome, descrição, preço e quantidade em estoque.
4. Cada pedido deve estar associado a um cliente.
5. Cada pedido pode conter um ou mais produtos.
6. O sistema deve registrar o status de cada pedido (em processamento, enviado, entregue, cancelado).
7. O sistema deve registrar pagamentos com forma de pagamento e data.

### 1.2 Regras de Negócio
- Um cliente pode fazer múltiplos pedidos.
- Um produto pode estar em vários pedidos.
- Um pedido pode conter múltiplos produtos (relação muitos-para-muitos).
- O estoque do produto deve ser atualizado após cada pedido concluído.
- Os produtos podem ser vendidos por terceiros.
- O pagamento deve estar associado a um pedido.
- Entrega – Possui status e código de rastreio.

### 1.3 Modelo Conceitual – E-commerce
Abaixo está a representação do modelo conceitual, usando a notação Entidade-Relacionamento (ER) com base nos requisitos levantados.
<div align="center">
    <img src="Files/img01.png" alt="Create a resource" width="600"/>
</div>

### 1.4 Entidades e Atributos
***Cliente***
- id_cliente (PK)
- tipo_cliente
- endereco
- email

***Cliente_PF (Entidade Fraca)***
- Cliente_id_cliente (FK)
- nome
- cpf
- data_nascimento
- celular

***Cliente_PJ (Entidade Fraca)***
- Cliente_id_cliente (FK)
- razao_social
- cnpj
- inscricao_estadual
- telefone

***Fornecedor***
- id_fornecedor (PK)
- razao_social
- endereco
- cnpj

***Produto***
- id_produto (PK)
- descricao
- preco
- estoque

***Pedido***
- id_pedido (PK)
- Cliente_id_cliente (FK)
- Produto_id_produto (FK)
- Entrega_id_entrega (FK)
- data_pedido
- status_pedido
- valor_pedido

***Pagamento***
- id_pagamento (PK)
- Pedido_id_pedido (FK)
- forma_pagamento
- data_pagamento
- status_pagamento

***Item_Pedido (Entidade Associativa)***
- id_pedido (FK)
- id_produto (FK)
- quantidade
- preco_unitario

***Entrega***
- id_entrega (PK)
- status
- data_entrega
- previsao_entrega
- rastreio
- endereco_entrega

### 1.5 Relacionamentos
- **Cliente 1:N Pedido** – Um cliente pode fazer vários pedidos.
- **Pedido 1:1 Pagamento** – Cada pedido possui um pagamento associado.
- **Pedido N:M Produto** – Representado pela entidade associativa `Item_Pedido`.

### 2.0 Refinando o Modelo Conceitual
A partir daqui serão documentados os ajustes e melhorias feitos após a construção inicial do modelo conceitual, sempre com base no que foi passado durante o modulo.

### 2.1 Primeiro Refinamento – Criação da Entidade Associativa "Item_Pedido"
- Motivação: A relação muitos-para-muitos entre Pedido e Produto precisava ser melhor representada.
- Solução: Criamos a entidade associativa "Item_Pedido", permitindo registrar quantidade e preço por item no pedido.

### 2.2 Refinamento 2 – Adição de status ao Pedido
- Motivação: Era necessário acompanhar o ciclo de vida de um pedido.
- Solução: Adicionado o atributo `status_pedido` na entidade Pedido (em processamento, enviado, entregue, cancelado). Para complementar o refinamento tambem foi adicionado o atributo data_pedido para registrar as datas em que cada um dos pedidos foram abertos.

### 2.3 Refinamento 3 – Registro da Forma de Pagamento
- Motivação: Era importante diferenciar pagamentos (cartão, boleto, pix etc.).
- Solução: Adicionado o atributo `forma_pagamento` na entidade Pagamento.


Outros refinamentos poderão ser realizados conforme novos requisitos forem identificados, ou correções sejam propostas no modulo.

### 3.0 Caso de Uso: Compra de um Produto
Criamos o ambiente e agora vamos realizar testes de funcionamento e ver se houve alguma falha ou falta na modelagem.

### 🧾 Cenário
O cliente João realiza uma compra de 2 unidades do produto "Fone Bluetooth".

### 3.1 Entidades Envolvidas

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



