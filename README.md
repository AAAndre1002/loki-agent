# Loki Agent (Android) — protótipo 0.2

Assistente Android open source, com entrada por voz, resposta falada, alguns comandos locais explícitos e ligação opcional a um endpoint de chat compatível com OpenAI (por exemplo, Ollama).

**Código-fonte completo:** [Loki-Agent-Android-v0.2.zip](./Loki-Agent-Android-v0.2.zip). As próximas versões serão publicadas no mesmo repositório.

## Estado atual

- Reconhecimento de voz em português (através do serviço de voz configurado no Android).
- Resposta por síntese de voz em português.
- Comandos locais allow-listed: abrir YouTube, WhatsApp, Maps, Chrome ou Definições; dizer as horas; pesquisar na web.
- Perguntas livres enviadas ao endpoint/modelo que o utilizador configurar.
- Serviço de Acessibilidade opcional com microfone flutuante para usar os controlos noutras apps: ler texto visível, subir/descer, voltar, abrir ecrã inicial e tocar num elemento com texto indicado — cada toque pede confirmação.
- Não executa ações sugeridas pelo modelo: respostas de IA são texto. A execução no telemóvel fica limitada a comandos explícitos e pré-definidos.

## Abrir no Android Studio

1. Instala Android Studio e JDK 17.
2. Abre a pasta `LokiAgent` como projeto Gradle.
3. Permite o download do Android Gradle Plugin e da plataforma SDK 35.
4. Liga o telemóvel com depuração USB ou usa um emulador e carrega em **Run**.
5. Permite o acesso ao microfone quando a app pedir.

## Ligar a Ollama

O Ollama tem de estar acessível na rede. No ecrã da app, configura o URL completo do endpoint `/v1/chat/completions`, por exemplo `http://192.168.1.20:11434/v1/chat/completions`, e o identificador do modelo instalado, como `qwen2.5:3b`.

- Substitui o IP pelo endereço real do computador/servidor.
- O telemóvel e o servidor têm de conseguir comunicar na mesma rede.
- O servidor tem de aceitar pedidos da rede local e disponibilizar a API OpenAI compatível.
- O URL é guardado localmente nas preferências da app. O texto do pedido é enviado para esse servidor quando o endpoint está configurado.
- Este protótipo permite HTTP para facilitar testes locais. Para uso público, configura HTTPS e autenticação; não exponhas Ollama diretamente à Internet.

## Ativar os controlos de acessibilidade

1. Abre a app e toca em **Ativar / gerir acessibilidade**.
2. Nas Definições do Android, escolhe **Loki Agent — controlos autorizados** e ativa o serviço.
3. Volta à app e deixa o serviço ativo. Deve aparecer um microfone flutuante sobre as outras apps.
4. Abre outra app, toca no microfone flutuante e diz **“lê o ecrã”**, **“desce”**, **“sobe”**, **“voltar”**, **“ecrã inicial”** ou **“toca em [texto]”**.
5. O toque num elemento apresenta uma confirmação antes de agir.

O serviço de acessibilidade pode ver o texto que o Android expõe no ecrã enquanto está ativo. O protótipo não guarda nem envia esse texto para o modelo; a leitura é apresentada/falada localmente. O Android e certas apps podem ocultar partes do conteúdo ou bloquear ações.

## Limites e segurança

Android exige consentimento explícito para a permissão especial de acessibilidade; algumas apps e operações continuam isoladas pelo sistema. Não há palavra de ativação nem escuta contínua: a voz só é captada quando tocas no microfone flutuante. Envio automático de mensagens, chamadas e ações financeiras não estão implementados. Respostas do modelo nunca são convertidas em ações no dispositivo.

## Licença

MIT — podes reutilizar e modificar este protótipo; o ficheiro `LICENSE` já está incluído.
