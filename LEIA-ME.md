# Ordens de Serviço: como colocar no ar

O app roda no navegador (computador e Android) e pode ser **instalado no celular** como um aplicativo.
As OS ficam gravadas no aparelho e são copiadas para a pasta **Ordens de Serviço** do seu **Google Drive**.
Assim todos os aparelhos conectados à mesma conta Google enxergam as mesmas OS.

Arquivos desta pasta: `index.html`, `manifest.json`, `sw.js`, `icon.svg`, `icon-192.png`, `icon-512.png`.

---

## 1. Publicar o app (grátis): GitHub Pages

O Android só instala o app e o Google só libera o Drive para um endereço **https**.

1. Crie uma conta em https://github.com (se ainda não tiver).
2. Clique em **New repository**, dê o nome `ordem-servico` e marque **Public**.
3. Clique em **uploading an existing file** e arraste os 6 arquivos acima. Depois clique em **Commit changes**.
4. Vá em **Settings → Pages**. Em *Branch*, escolha `main` e `/ (root)` e clique em **Save**.
5. Depois de 1 a 2 minutos o app estará em: `https://contatomactecnology-wq.github.io/ordem-servico/`

> Netlify (arrastar a pasta em https://app.netlify.com/drop) também funciona.

As OS **não** ficam no GitHub, só o programa. Os dados ficam no aparelho e no seu Drive.

## 2. Criar o acesso ao Google Drive (uma vez só)

1. Acesse https://console.cloud.google.com e crie um projeto (ex.: "Ordem de Servico").
2. **APIs e serviços → Biblioteca**: procure **Google Drive API** e clique em **Ativar**.
3. **APIs e serviços → Tela de consentimento OAuth**:
   - Tipo: **Externo**. Preencha o nome do app e o seu e-mail.
   - Em **Usuários de teste**, adicione o seu e-mail do Google (e o de quem mais for usar).
4. **APIs e serviços → Credenciais → Criar credenciais → ID do cliente OAuth**:
   - Tipo: **Aplicativo da Web**
   - **Origens JavaScript autorizadas**: `https://contatomactecnology-wq.github.io`
     (para testar no PC, adicione também `http://localhost:8765`)
   - Clique em **Criar** e copie o **ID do cliente** (termina em `.apps.googleusercontent.com`).

## 3. Usar

1. Abra o endereço do app, toque em **⚙️**, cole o **Client ID** e salve.
2. Toque em **☁️ Conectar Drive** e entre com sua conta Google.
3. **No Android**: abra o endereço no Chrome, toque no menu **⋮ → Instalar app** (ou "Adicionar à tela inicial").
   Repita o passo 1 no celular (o Client ID fica salvo em cada aparelho).

### Como funciona a sincronização
- Ao salvar uma OS conectado, ela vai para o Drive em seguida.
- Ao abrir o app, toque em **☁️** para baixar o que foi feito em outros aparelhos.
  O Google pede o login de novo a cada 1 hora, mais ou menos.
- Sem internet o app continua funcionando. Depois, toque em **☁️ Sincronizar (pendente)**.
- Antes de criar uma OS nova, o app consulta o Drive para **não repetir o número**.
  Se dois aparelhos criarem OS **sem internet** ao mesmo tempo, o número pode repetir. Nesse caso, edite uma delas.
- Cada OS vira um arquivo `OS-2026-0001.json` (com as fotos) na pasta **Ordens de Serviço** do Drive.

### Etiqueta de garantia
Na OS, toque em **🏷️ Etiqueta de garantia**. A etiqueta tem 60 mm e traz o número da OS, um código de barras
e a data de validade da garantia (data de saída + dias de garantia). Imprima numa impressora de etiquetas
ou recorte de uma folha A4.

### Backup extra
O botão **Backup** baixa um arquivo `.json` com todas as OS. Para recuperar, use **Restaurar**.
