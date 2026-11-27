# Changelog — NoxisTV

Todas as novidades notáveis do **NoxisTV** para Android são documentadas aqui.  
*All notable user-facing updates to **NoxisTV** for Android are documented here.*

---

## [v1.3.0] — 2026-11-27 — Dark Cinema, Miniplayer/PiP, EPG Leve & Smart Channel

### ⚡ Smart Channel, Auto Failover & Resiliência
- **Smart Channel (Agrupamento de Variantes):** Agrupa visualmente variantes do mesmo canal (`FHD`, `HD`, `4K`, `H265`, `SD`, `ALT`) com badge discreto (`FHD • 3 fontes`), seletor rápido no player e memória da última qualidade escolhida.
- **Auto Source Failover:** Em caso de queda definitiva do sinal atual, alterna automaticamente para a próxima fonte do mesmo canal sem fechar o player e com proteção contra loop infinito.
- **Detecção Automática `get.php` (M3U → Xtream):** Detecta URLs Xtream coladas na aba M3U e oferece conexão via API Xtream com 1 toque.
- **Botão "Recarregar"** nos controles do player para reconexão limpa mantendo a posição em VOD.
- **Tela de Erro Acionável:** Causa provável clara (`HTTP 403/401/404/5xx`, `Timeout`, `Codec`) com ações diretas (**Tentar novamente**, **Trocar fonte** e **Trocar User-Agent** sem sair do player).
- **Resumo de Alterações ao Atualizar Lista:** Exibe o diff real antes/depois (ex.: `+12 canais, +38 filmes, +4 séries` ou `nenhuma alteração`).

### 📺 EPG Leve XMLTV (Streaming O(1))
- Suporte nativo a guias **XMLTV `.xml` e `.xml.gz`** em streaming puro (compatível com dispositivos de baixa RAM).
- Auto-descoberta de `url-tvg` / `x-tvg-url` em listas M3U e `xmltv.php` em contas Xtream Codes.
- Casamento inteligente (*Smart Match*) por `tvg-id` + fallback por nome normalizado.
- Ajuste manual de URL de EPG, fuso horário (`-6h` a `+6h` em passos de 30 min) e botão **Atualizar EPG**.
- Exibição discreta **"Agora no ar"** + barra fina de progresso na lista Ao Vivo e na gaveta do player, além de **"Agora + A seguir"** no overlay do player.

### 🎬 Miniplayer Flutuante, PiP & Melhorias no Player
- **Miniplayer Flutuante 16:9** interno sobre todo o app + **Picture-in-Picture (PiP)** nativo do Android.
- **Botão "Canal Anterior"** (1 toque) no Ao Vivo e **Gaveta de Episódios/Temporadas** em Séries.
- **Velocidade de reprodução VOD/Séries** de `0.5x` a `2.0x` (incluindo `0.75x`).
- **Legendas configuráveis** (tamanho e estilo de fundo) e painel translúcido **"Saúde da Reprodução"** (resolução, FPS, codec, bitrate e buffer).
- Carregamento Cinemático suave antes do primeiro frame e Sleep Timer (Temporizador).

### 📂 Catálogo, Playlists & Performance
- **Identidade NoxisTV Dark Cinema**, troca rápida de lista e botão **`+`** direto no cabeçalho principal.
- **Pausar/Reativar playlists** sem perder favoritos ou histórico, **Fixar grupos no topo**, filtro de grupos **A–Z** e **Limpeza automática de títulos** (`TitleCleaner`).
- Marcar manualmente como **Assistido / Não assistido** e **Remover de "Continuar Assistindo"**.
- Leitura de validade e limite de conexões em contas **Xtream Codes**.
- Gestão do cache de imagens em disco direto nas Configurações.
- **Home < 25 ms** em bancos com **200.000+ itens** e importação de backup JSON em lote único sem N+1.

---

## [v1.0.0 – v1.2.2] — Fundação Offline-First & Blindagem
- Motor de ingestão 100% em streaming para **M3U / M3U8** e **Xtream Codes API** com banco **Room + SQLite WAL + FTS5**.
- Pré-importação inteligente com seleção de grupos (`+18` desmarcados por padrão).
- Atualização e exclusão atômicas de múltiplas playlists.
- **Controle Parental com PIN** (zero vazamentos na Home, Catálogo, Favoritos e Busca).
- Backup e restauração local em `.json` (favoritos e progresso).
