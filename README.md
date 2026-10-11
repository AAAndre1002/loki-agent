# Loki Agent para Android — v0.3.0

Assistente Android open source com comandos de voz, ações locais explícitas, controlos de acessibilidade opcionais e ligação a modelos compatíveis com Ollama.

**Código-fonte:** [Loki-Agent-Android-v0.3.0.zip](./Loki-Agent-Android-v0.3.0.zip)

## Funcionalidades

- Reconhecimento e resposta por voz em português.
- Abre aplicações pelo nome visível no launcher, além de atalhos conhecidos.
- Pesquisa na web e consulta as horas.
- Ligação opcional ao Ollama ou a outro endpoint compatível com a API OpenAI.
- Serviço opcional de Acessibilidade para ler texto exposto no ecrã, navegar e tocar num elemento indicado. Cada toque exige confirmação.
- As respostas do modelo nunca são executadas como comandos.

## Descarregar o APK de teste

1. Abre o separador **Actions** deste repositório.
2. Escolhe a execução mais recente do workflow **Build Android APK** e confirma que terminou com sucesso.
3. Na página da execução, descarrega o artefacto **Loki-Agent-debug-APK**.

O artefacto fica disponível durante 14 dias. É um APK de depuração para testes, não uma versão de lançamento assinada para publicação. Se ainda não existir uma execução concluída com sucesso, aguarda que a compilação termine.

## Compilar localmente

Extrai o ZIP e abre a pasta `LokiAgent` no Android Studio, com JDK 17 e Android SDK 35. Também podes escolher **Build → Build Bundle(s) / APK(s) → Build APK(s)**. O APK debug é criado em `app/build/outputs/apk/debug/app-debug.apk`.

## Configurar Ollama

Na app, indica o URL completo do endpoint `/v1/chat/completions` (por exemplo `http://192.168.1.20:11434/v1/chat/completions`) e o nome de um modelo instalado, como `qwen2.5:3b`. O telemóvel e o servidor têm de estar na mesma rede. Não exponhas Ollama diretamente à Internet; usa HTTPS e autenticação para acessos remotos.

## Acessibilidade e segurança

A Acessibilidade é opcional e tem de ser ativada manualmente nas Definições do Android. Enquanto ativa, o serviço pode ler texto que o sistema expõe, mas este protótipo não o guarda nem o envia ao modelo. Algumas aplicações ocultam conteúdo ou bloqueiam controlos. Não há palavra de ativação nem escuta contínua. Chamadas, mensagens e ações financeiras não são executadas automaticamente.

Licença MIT — ver [`LICENSE`](./LICENSE).
