# Canal NR-1 Diu Vitae — Guia de Deploy
## Vercel + Firebase Firestore

---

## 1. Firebase — Configurar o Firestore

1. Acesse https://console.firebase.google.com → projeto **dnr1-90cad**
2. Vá em **Firestore Database** → Criar banco de dados
   - Modo: **Produção**
   - Região: `us-east1` (ou `southamerica-east1` para latência menor)
3. Vá em **Regras** e cole o conteúdo do arquivo `firestore.rules`
4. Publique as regras

### Coleções criadas automaticamente pelo app:
| Coleção | Conteúdo |
|---|---|
| `relatos` | Todos os relatos enviados pelos colaboradores |
| `manual_data` | Registros manuais inseridos pelo RH |
| `config` | Configurações (texto de clima/ação corretiva) |

---

## 2. Deploy no Vercel (mais simples)

### Opção A — Upload direto (sem GitHub)
1. Acesse https://vercel.com → New Project → **Browse**
2. Faça upload da pasta `nr1-diuvitae/`
3. Framework Preset: **Other**
4. Root Directory: deixe vazio
5. Clique em **Deploy**

### Opção B — Via GitHub
1. Crie repositório no GitHub e suba a pasta `nr1-diuvitae/`
2. No Vercel: New Project → importe o repositório
3. Framework: Other → Deploy

### Domínio personalizado (opcional)
- No Vercel: Settings → Domains → adicione `nr1.diuvitae.com.br`
- Aponte o DNS do seu domínio para o Vercel

---

## 3. Acesso ao painel

- **URL do colaborador:** `https://seu-projeto.vercel.app`
- **Painel RH:** clique em "Painel RH" no header
- **Senha:** `diuvitae182`

---

## 4. Índices do Firestore (se necessário)

Se aparecer erro de índice no console, acesse o link que o Firebase gera
automaticamente e crie os índices compostos:

```
relatos: createdAt DESC
relatos: date ASC + status ASC
```

---

## 5. Backup de dados

Para exportar todos os relatos:
1. Firebase Console → Firestore → **Exportar dados**
2. Ou use o botão "Baixar PDF" no painel para relatórios mensais

---

## 6. Próximos passos recomendados

- [ ] Adicionar Firebase Authentication para o painel (substituir senha client-side)
- [ ] Ativar Firebase App Check para proteção extra
- [ ] Configurar alertas por e-mail via Firebase Functions quando novo relato chegar
- [ ] Adicionar domínio personalizado no Vercel

---

**Suporte:** casaderepouso@diuvitae.com.br
