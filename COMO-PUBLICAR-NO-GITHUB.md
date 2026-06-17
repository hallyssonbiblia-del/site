# Site grátis (GitHub Pages) + TikTok automático

O TikTok exige um site com Política de Privacidade e Termos. Aqui montamos um
**grátis** no GitHub Pages e ligamos a publicação automática.

Troque `SEUUSUARIO` pelo seu nome de usuário do GitHub em todos os passos.

## 1. Criar o site (uma vez)

1. Crie uma conta em https://github.com (grátis), se ainda não tiver.
2. Crie um repositório **público** com o nome EXATO: `SEUUSUARIO.github.io`
3. Suba o CONTEÚDO desta pasta `site/` para o repositório (botão
   **Add file → Upload files**, arraste tudo, inclusive as pastas, e **Commit**):
   - `index.html`, `style.css`, as pastas `privacidade/`, `termos/`, `callback/`
     e os arquivos `tiktok...txt` (verificação).
4. Vá em **Settings → Pages** → em *Build and deployment*, Source = **Deploy from a
   branch**, Branch = **main** / **/(root)** → **Save**. Aguarde ~1 minuto.
5. Seu site fica em: `https://SEUUSUARIO.github.io/`

As URLs (agora em pasta, mais limpas):
- Termos:       `https://SEUUSUARIO.github.io/termos/`
- Privacidade:  `https://SEUUSUARIO.github.io/privacidade/`
- Callback:     `https://SEUUSUARIO.github.io/callback/`

## 2. Preencher no app do TikTok (developers.tiktok.com)

- **Terms of Service URL**: `https://SEUUSUARIO.github.io/termos/`
- **Privacy Policy URL**:   `https://SEUUSUARIO.github.io/privacidade/`
- **Verify URL properties**: o TikTok dá um arquivo `tiktokXXXX.txt`. Ele já está
  nesta pasta — depois do upload ficará em `https://SEUUSUARIO.github.io/tiktokXXXX.txt`.
  Clique em **Verify**.
- Em **Login Kit → Redirect URI**, adicione:
  `https://SEUUSUARIO.github.io/callback/`
- Adicione os **scopes**: `video.upload` (e `video.publish` se for usar modo direct).
- Se o app estiver em **Sandbox**, adicione sua conta em **Target Users**.

## 3. Apontar o programa para o seu site

No `config.yaml`, seção `tiktok:`, troque:

```yaml
tiktok:
  redirect_uri: "https://SEUUSUARIO.github.io/callback/"
```

## 4. Conectar e ligar

No PowerShell (para conseguir COLAR o código):

```powershell
cd C:\Sites\oracao-diaria
.\.venv\Scripts\oracao.exe tiktok login
```

- Abre o navegador → Autorizar → cai na página de callback que mostra o **código**.
- Copie o código e cole no terminal, na linha "Cole aqui o código".

Depois, no `config.yaml`: `plataformas: → tiktok: true`. Pronto — `oracao dia`
passa a subir os Shorts pro TikTok (no modo `inbox` eles caem nos Rascunhos; você
abre o app e dá um toque em Postar).
