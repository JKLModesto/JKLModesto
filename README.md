# 👋 Olá, eu sou **Pedro Modesto**

**Backend Engineer · Node.js | TypeScript | Arquitetura de Sistemas**

Construo APIs rápidas, seguras e observáveis. Banco de dados bem modelados, filas que não engasgam e deploy sem drama.

&#x20; &#x20;

---

## ⚡ Sobre mim

- 🇧🇷 **Backend** com foco em **Node.js + TypeScript** e arquitetura escalável (Clean/Hexagonal).
- **DB first**: modelagem sólida, migrações previsíveis e performance antes de otimizações prematuras.
- **Observabilidade**: logs estruturados, métricas e tracing desde o dia 0.
- **DX >** tudo: código claro, padrões consistentes, documentado e testável.

> "Simplicidade que aguenta porrada." — meu princípio para serviços em produção.

---

## 🧰 Stack principal

**Linguagens & Runtime**

&#x20;

**Frameworks & Libs**

&#x20; &#x20;

**ORM / SQL**

&#x20;&#x20;

**Mensageria & Jobs**

&#x20;&#x20;

**Infra & Observabilidade**

&#x20; &#x20;

**IA & Automação**

&#x20;

---

## 📌 Agora (Atualizado em 11/08/2025)

- Estudando **NestJS** avançado (pipes, interceptors, modules dinâmicos, CQRS) e **Prisma** (transações, middlewares, migrations sólidas).
- Aprofundando **padrões distribuídos**: Pub/Sub, Circuit Breaker, Idempotência, Retry/Backoff, Outbox.
- Brincando com **agentes de IA** e automações no **n8n**.

---

## 🧭 Princípios de engenharia

- **Arquitetura limpa** e modular (domínios primeiro).
- **Contratos explícitos** (DTOs + validação + tipagem end‑to‑end).
- **Fail fast**: erros claros, tratáveis e observáveis.
- **Defesa em profundidade**: authn/authz, rate limit, tenancy, políticas de dados.
- **Automação de tudo**: linters, formatters, CI/CD e verificação de qualidade.

---

## 🔎 Destaques (projetos)

- **api‑starter-nest-prisma** — Template de API com NestJS + Prisma + Docker + CI. *Batteries included.*\
  `Auth JWT · RBAC · Swagger · Migrations · Seeds · Testes · OTel`
- **queue‑workshop‑bullmq** — Padrões com BullMQ (retry/backoff, jobs idempotentes, DLQ).
- **ai‑agents‑n8n** — Fluxos de agentes IA para atendimento/SDR e follow‑ups.

> 📁 Substitua os nomes acima pelos seus repositórios reais e links.

---

## 🧪 Um gostinho do meu código

```ts
// Exemplo condensado de um serviço Nest que orquestra DB + fila + tracing
@Injectable()
export class OrdersService {
  constructor(
    private readonly prisma: PrismaService,
    @InjectQueue('billing') private readonly billing: Queue,
  ) {}

  async createOrder(input: CreateOrderDto, userId: string) {
    return this.prisma.$transaction(async (tx) => {
      const order = await tx.order.create({ data: { ...input, userId } });

      // enqueue job com idempotência
      await this.billing.add(
        'charge',
        { orderId: order.id },
        { jobId: `charge:${order.id}`, removeOnComplete: true, attempts: 5, backoff: { type: 'exponential', delay: 1000 } }
      );

      return order;
    });
  }
}
```

---

## 📈 Como eu trabalho

- **Tests first** quando o domínio é crítico; caso contrário, **risk‑based testing**.
- **Observabilidade por padrão**: logs estruturados + métricas + traces com correlação.
- **Documentação viva** (OpenAPI + README por serviço + ADRs curtos).
- **Perf consciente**: índices certos, N+1 sob controle, limites e timeouts na borda.

---

## 🤝 Vamos conversar?

- 💼 **Vagas / freelas**: abra uma *issue* neste repo ou me chame no **LinkedIn**.
- ✉️ **Email**: [SEUEMAIL@exemplo.com](mailto\:SEUEMAIL@exemplo.com)
- 💬 **DM**: @SEUUSUARIO (Twitter/Bluesky/Threads)

---

## 🧩 Extras opcionais

---

### 🛠️ Como usar este template

1. Procure por `SEU NOME AQUI`, `SEU_GITHUB`, `SEU-LINKEDIN`, `SEUEMAIL@exemplo.com`, etc., e substitua pelos seus dados.
2. Troque o bloco **Destaques** pelos seus repositórios e links.
3. (Opcional) Descomente as **Métricas públicas** se curtir.
4. Commit como `README.md` no repositório com o mesmo nome do seu usuário no GitHub.

> Dúvidas ou quer uma versão ainda mais personalizada? Me diga seu usuário do GitHub, links e 3 projetos dos quais você mais se orgulha.
