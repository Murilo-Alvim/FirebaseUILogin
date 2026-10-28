# Passo a passo: o que você precisa fazer

O código está pronto. Falta só a parte do Firebase, que depende da sua conta Google.

1. Abra o projeto no Android Studio (File > Open > pasta FirebaseUILogin) e espere o Gradle sincronizar. Vai dar erro de "google-services.json missing". Isso é esperado.
2. Pegue o SHA-1: aba Gradle (lado direito) > ícone do terminal "Execute Gradle Task" > digite `signingReport` > Enter. Ou no Terminal: `./gradlew signingReport` (Windows: `gradlew signingReport`). Copie a linha SHA1 da variante debug.
3. No https://console.firebase.google.com: crie um projeto, clique no ícone Android e preencha:
   - Nome do pacote: br.universidade.projeto
   - SHA-1: cole o valor copiado
   - Clique em Registrar app
4. No console, vá em Authentication > Começar > Método de login. Ative E-mail/senha e Google (no Google, escolha um e-mail de suporte e salve).
5. Vá em Authentication > Configurações > Ações do usuário e DESMARQUE "Proteção contra enumeração de e-mail". Sem isso o FirebaseUI não consegue diferenciar login de cadastro.
6. Vá em Configurações do projeto (engrenagem) > Seus apps e baixe o google-services.json. Baixe agora, depois dos passos 3 a 5, para ele já vir com a configuração do Google.
7. Coloque o arquivo em FirebaseUILogin/app/google-services.json (a pasta app, ao lado do build.gradle.kts dela).
8. No Android Studio, clique em "Sync Project with Gradle Files" (ícone do elefante) e rode o app (▶) em um emulador que tenha Google Play (ícone da Play Store no Device Manager).

## Teste
- Entrar com e-mail novo: abre o cadastro (nome + senha) e o usuário aparece em Authentication > Usuários.
- Entrar com Google: escolha a conta.
- Botão Sair: volta para a tela de login.
