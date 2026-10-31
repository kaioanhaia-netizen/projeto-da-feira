# Hexatech

**Sistema de e-commerce e gestão para varejo de hardware e eletrônicos**

Controle de estoque, pedidos em Kanban, fichas de cliente e painel administrativo — em uma plataforma integrada.

---

## Equipe

| Nome | Responsabilidade |
|------|------------------|
| **Kaio Padilha** | Coordenação e integração Firebase |
| **Pedro Augusto** | Front-end do site de vendas |
| **João Monteiro** | Front-end do painel administrativo |
| **João Bomfim** | Regras de negócio (pedidos, estoque, status) |
| **Rafael Assunção** | Design, protótipos e documentação |

**Projeto Integrador** — 2025/2026

---

## O que é a Hexatech?

A Hexatech é uma solução digital para lojas de **componentes eletrônicos, ferramentas e periféricos**. O projeto une dois ambientes:

1. **Site de vendas (Landing)** — apresentação do produto, captura de leads e vitrine conceitual  
2. **Painel administrativo** — gestão de pedidos, estoque e configurações da loja  

### Objetivos

- Organizar pedidos em etapas: **Esperando → Em Andamento → Entregue**
- Controlar estoque em tempo real (quantidade, preços, alertas de mínimo)
- Reduzir erros e divergências entre venda e estoque
- Oferecer ao administrador controle total sobre fluxos e configurações

---

## Estrutura do projeto

```text
hexatech/
├── index.html                          # Site de vendas / Landing page
├── sistema.html                        # Painel administrativo
├── Relatorio_Tecnico_Hexatech.pdf      # Relatório técnico final
└── README.md                           # Este arquivo
```

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Landing page completa (hero, soluções, tour, CTA, footer) |
| `sistema.html` | Painel com login, dashboard, pedidos, ficha e admin |
| `Relatorio_Tecnico_Hexatech.pdf` | Documentação técnica do projeto integrador |

---

## Como executar

Não é necessário instalar dependências nem rodar servidor.

1. Baixe ou clone os arquivos HTML  
2. Abra no navegador:
   - **Site de vendas:** clique duas vezes em `index.html`
   - **Painel:** clique duas vezes em `sistema.html`

> Recomendado: Google Chrome ou Microsoft Edge.

### Login do painel



| Usuário | `adm` |
| Senha | `123456` |

---

## Funcionalidades

### Site de vendas (`index.html`)

- Header fixo com menu responsivo  
- Hero com mockup do dashboard  
- Seção de soluções (Atendimento Ágil, Precisão, Capital Otimizado)  
- Tour interativo da plataforma  
- Formulário de captura de leads  
- Design dark (navy + ciano elétrico), 100% responsivo  

### Painel administrativo (`sistema.html`)

| Módulo | O que faz |
|--------|-----------|
| **Dashboard** | Totais de pedidos + lista de estoque + formulário de novo item |
| **Pedidos** | Kanban (Esperando / Em Andamento / Entregue), arrastar cards, apagar, limpar entregues |
| **Nova Ficha** | Cadastro de pedido do cliente (entra como “Esperando”) |
| **Estoque** | Adicionar item, alterar quantidade (+/−), remover item |
| **Admin** | Editar fluxos de venda/troca e configurações da loja |

---

## Tecnologias

| Camada | Tecnologia |
|--------|------------|
| Markup | HTML5 |
| Estilo | Tailwind CSS (CDN) |
| Scripts | JavaScript (ES modules) |
| Ícones | Lucide Icons |
| Fonte | Plus Jakarta Sans |
| Banco de dados | Firebase Firestore |
| Persistência local | localStorage (fallback) |

### Firebase

Projeto: **projeto-do-kaio**

Coleções utilizadas:

| Coleção | Uso |
|---------|-----|
| `pedidos` | Fichas / pedidos do Kanban |
| `estoque` | Produtos e quantidades |
| `leads` | E-mails capturados na landing |

---

## Identidade visual

| Token | Valor |
|-------|--------|
| Fundo principal | `#0B132B` |
| Cards / seções | `#1C2541` |
| Acento (CTA) | `#00F0FF` (ciano elétrico) |
| Texto claro | `#FFFFFF` / `#E2E8F0` |
| Border radius | 12px – 16px |

Estilo: SaaS / Enterprise B2B, dark theme, microinterações sutis.

---

## Fluxo principal de pedido

```text
Cliente preenche a Ficha
        ↓
Pedido criado (status: esperando)  →  Firebase + tela Kanban
        ↓
Equipe move para "Em Andamento"
        ↓
Pedido finalizado → "Entregue"
        ↓
Estoque pode ser ajustado no Dashboard
```

---

## Modelo de dados (resumo)

### `pedidos`
`numero`, `clienteNome`, `telefone`, `produto`, `quantidade`, `observacoes`, `status`, `criadoEm`, `atualizadoEm`

### `estoque`
`nome`, `quantidade`, `minima`, `custo`, `venda`, `local`, `criadoEm`

### `leads`
`email`, `criadoEm`

---

## Segurança (versão acadêmica)

- Login de administrador no painel (validação em sessionStorage)  
- Em produção: recomenda-se **Firebase Authentication** e regras de segurança no Firestore restritas por usuário  

Exemplo de regras Firestore (desenvolvimento):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true; // restringir em produção
    }
  }
}
```

---

## Melhorias futuras

- [ ] Firebase Auth com múltiplos perfis (admin, operador, cliente)  
- [ ] Carrinho multi-item e pagamento online (Pix / cartão)  
- [ ] Baixa automática de estoque na finalização do pedido  
- [ ] Relatórios de vendas e alertas de recompra  
- [ ] PWA / app mobile para o balcão  
- [ ] Testes automatizados e CI/CD  

---

## Documentação adicional

Consulte o **Relatório Técnico Final** (`Relatorio_Tecnico_Hexatech.pdf`) para:

1. Capa e identificação da equipe  
2. Introdução e escopo  
3. Front-end e protótipo  
4. Modelagem do banco de dados (DER + dicionário)  
5. Arquitetura back-end e rotas  
6. Conclusão e melhorias  

---

## Licença

Projeto acadêmico — Projeto Integrador.  
Uso educacional. Todos os direitos reservados à equipe Hexatech.

---

**Hexatech** — controle total, eficiência e confiabilidade no varejo de hardware.
