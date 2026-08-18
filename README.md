# Duarttes Tech — Site institucional

Landing page oficial da **Duarttes Tech** — engenharia digital para negócios de
Americana e região (construir · operar · monitorar).

Site estático, arquivo único, sem dependências. Carrega rápido e roda em qualquer
hospedagem.

**Produção:** https://duarttestech.com

---

## Estrutura

```
site-duarttestech/
├── index.html        # a landing page inteira (HTML + CSS + JS num arquivo só)
├── assets/           # imagens, favicon, logos (adicionar aqui quando tiver)
├── .cpanel.yml       # deploy automático no HostGator via Git
├── .gitignore
└── README.md
```

---

## Rodar localmente

O site é estático — basta abrir o `index.html` no navegador. Para simular um
servidor real (recomendado):

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```

---

## Publicar no HostGator

Existem duas formas. Para um site de uma página, a **A** já resolve.

### A) Upload manual (mais simples)

1. Acesse o **cPanel** do HostGator.
2. **Gerenciador de Arquivos** → pasta `public_html`.
3. Envie o `index.html` (e a pasta `assets/`, quando existir).
4. Pronto — `duarttestech.com` no ar.

> Alternativa: FTP/SFTP com as credenciais do cPanel, apontando para `public_html`.

### B) Deploy via Git (mantém tudo versionado)

Se o seu plano tiver o recurso **Git™ Version Control** no cPanel:

1. cPanel → **Git Version Control** → **Criar repositório**.
2. Aponte para este repositório (clone do seu GitHub) ou faça push para o repo do servidor.
3. O arquivo `.cpanel.yml` (incluso) copia os arquivos para `public_html` a cada deploy.

Antes, edite **uma linha** no `.cpanel.yml`, trocando `USUARIO` pelo seu usuário do cPanel:

```yaml
- export DEPLOYPATH=/home/USUARIO/public_html/
```

---

## ✅ Checklist antes de publicar

Coisas ainda marcadas como placeholder no `index.html` (busca-e-substitui):

- [ ] **WhatsApp** — trocar `55XXXXXXXXXXX` pelo número do chip da empresa
      (aparece em 8 lugares: menu, hero, os 3 planos, CTA final e botão flutuante).
- [ ] **Valores dos planos** — trocar os `R$ —` de Essencial / Pro / Gestão.
- [ ] **Cases** — nada obrigatório agora; adicionar projetos reais quando tiver.
- [ ] **Favicon e logo** — colocar em `assets/` e referenciar no `<head>`.

---

## Domínio e contato

- **Domínio:** duarttestech.com (HostGator)
- **E-mail:** contato@duarttestech.com
- **Instagram:** @duarttes.tech

---

## Organização dos repositórios (Duarttes Tech)

Padrão para crescer sem virar bagunça — uma **organização** no GitHub
(`duarttes-tech`) com um repositório por finalidade:

| Repositório              | Para quê                                            |
|--------------------------|-----------------------------------------------------|
| `site-duarttestech`      | Este site (o próprio negócio)                        |
| `template-site-cliente`  | Boilerplate para clonar e começar cada projeto rápido |
| `cliente-<nome>`         | Um repo por cliente (ex.: `cliente-oficinadojoao`)  |

**Regra de ouro:** credencial nunca entra no Git. Use `.env` + `.gitignore` —
principalmente ao adicionar bots, GLPI e monitoramento.

---

## Roadmap de infraestrutura

- **Sites estáticos** → HostGator (este repo).
- **Camada Operar/Monitorar** (GLPI, Zabbix, Grafana) → exige **VPS**; não roda
  em hospedagem compartilhada. Planejar quando o primeiro cliente de assinatura
  fechar.

---

## Convenção de commits (sugestão)

```
feat:  nova seção ou funcionalidade
fix:   correção
style: ajuste visual / CSS
docs:  README e documentação
chore: manutenção, deploy, config
```
