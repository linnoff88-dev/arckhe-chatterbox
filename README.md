![Chatterbox Turbo Image](./Chatterbox-Turbo.jpg)

# Chatterbox TTS

[![Ouvir demos](https://img.shields.io/badge/ouvir-demos_de_Ã¡udio-blue)](https://resemble-ai.github.io/chatterbox_turbo_demopage/)
[![HuggingFace Spaces](https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-sm.svg)](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo)
[![AvaliaÃ§Ã£o Podonos](https://static-public.podonos.com/badges/insight-on-pdns-sm-dark.svg)](https://podonos.com/resembleai/chatterbox)
[![Discord](https://img.shields.io/discord/1377773249798344776?label=entrar%20no%20discord&logo=discord&style=flat)](https://discord.gg/rJq9cRJBJ6)
[![LicenÃ§a MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-green)](LICENSE)
[![Downloads HF](https://img.shields.io/badge/downloads-1M%2B-orange)](https://huggingface.co/ResembleAI)
[![GitHub Stars](https://img.shields.io/github/stars/resemble-ai/chatterbox?style=flat&label=stars)](https://github.com/resemble-ai/chatterbox)

_Desenvolvido com â™¥ï¸ por <a href="https://resemble.ai" target="_blank"><img width="100" alt="resemble-logo" src="https://github.com/user-attachments/assets/35cf756b-3506-4943-9c72-c05ddfa4e525" /></a>_

---

## O que Ã© o Chatterbox?

**Chatterbox** Ã© uma famÃ­lia de trÃªs modelos de sÃ­ntese de voz (TTS) de cÃ³digo aberto, estado da arte, desenvolvidos pela **Resemble AI**. LanÃ§ado sob licenÃ§a **MIT** (uso comercial livre), o Chatterbox ultrapassou **1 milhÃ£o de downloads** no HuggingFace e superou soluÃ§Ãµes comerciais como ElevenLabs em testes cegos â€” com **63,75% de preferÃªncia dos usuÃ¡rios**.

### HistÃ³rico de LanÃ§amentos

| Data | Evento |
|------|--------|
| **Maio 2025** | LanÃ§amento do **Chatterbox** original (500M, inglÃªs, MIT) â€” primeiro TTS open-source com controle de exageraÃ§Ã£o emocional. Atingiu 11.000+ estrelas no GitHub em poucas semanas |
| **Setembro 2025** | LanÃ§amento do **Chatterbox-Multilingual** (500M, 23 idiomas) |
| **Dezembro 2025** | LanÃ§amento do **Chatterbox-Turbo** (350M, inglÃªs) â€” avaliaÃ§Ã£o Podonos publicada em 12/12/2025. Superou ElevenLabs em 63,75% de preferÃªncia |

### Por que escolher o Chatterbox?

| CritÃ©rio | Chatterbox | ElevenLabs / Cartesia |
|----------|-----------|----------------------|
| LicenÃ§a | **MIT (gratuito e comercial)** | ProprietÃ¡rio (pago) |
| Voice Clone | **Zero-shot, sem treinamento** | Requer conta paga |
| Qualidade | **Avaliado superior em testes cegos** | ReferÃªncia de mercado |
| Self-hosted | **Sim, 100% offline** | NÃ£o |
| Watermark IA | **Sim (Perth, imperceptÃ­vel)** | NÃ£o |
| Idiomas | **23 idiomas (modelo MTL)** | Varia por plano |

---

## FamÃ­lia de Modelos

<img width="1200" height="600" alt="Podonos Turbo Eval" src="https://storage.googleapis.com/chatterbox-demo-samples/turbo/podonos_turbo.png" />

### âš¡ Comparativo dos Modelos

| Modelo | ParÃ¢metros | Idiomas | Destaques | Melhor Para | Demo | Exemplos |
|:-------|:----------:|:-------:|:----------|:------------|:----:|:--------:|
| **Chatterbox-Turbo** | **350M** | **InglÃªs** | Tags paralingÃ¼Ã­sticas, 1-step decoder, menor VRAM | Voice agents em tempo real, produÃ§Ã£o | [Demo](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo) | [Ouvir](https://resemble-ai.github.io/chatterbox_turbo_demopage/) |
| **Chatterbox-Multilingual** | 500M | **23 idiomas** | Zero-shot cloning cross-language, backbone Llama | LocalizaÃ§Ã£o, dublagem, aplicaÃ§Ãµes globais | [Demo](https://huggingface.co/spaces/ResembleAI/Chatterbox-Multilingual-TTS) | [Ouvir](https://resemble-ai.github.io/chatterbox_demopage/) |
| **Chatterbox** (English) | 500M | InglÃªs | Controles CFG e Exaggeration, backbone Llama | TTS criativo, controle expressivo fino | [Demo](https://huggingface.co/spaces/ResembleAI/Chatterbox) | [Ouvir](https://resemble-ai.github.io/chatterbox_demopage/) |

---

## Arquitetura TÃ©cnica

O pipeline segue dois estÃ¡gios principais:

```
Texto + Embedding de Voz (256-dim)
         â”‚
         â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   T3 (LLM)          â”‚  GPT2 (Turbo) ou Llama (English/MTL)
â”‚   Texto â†’ Tokens    â”‚  VocabulÃ¡rio: 704 (EN) / 2454 (MTL)
â”‚   de Fala @ 25 Hz   â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
         â”‚
         â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   S3Gen (CFM)        â”‚  Flow Matching (Diffusion)
â”‚   Tokens â†’ Mel       â”‚  1 step (Turbo) ou 10 steps (outros)
â”‚   Spectrograma       â”‚  Entrada: S3_SR = 16.000 Hz
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
         â”‚
         â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   HiFiGAN Vocoder   â”‚  Mel â†’ Ãudio WAV
â”‚   SaÃ­da @ 24 kHz    â”‚  S3GEN_SR = 24.000 Hz
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
         â”‚
         â–¼
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚   Perth Watermark   â”‚  Marca d'Ã¡gua neural imperceptÃ­vel
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### Detalhes por Componente

**T3 â€” Text-to-Speech-Token:**
- Backbone: GPT2 (Turbo / 350M) ou Llama (English & MTL / 500M)
- Taxa de saÃ­da: 25 Hz de tokens de fala
- Condicionado por: tokens de texto + embedding de locutor (256 dims)
- Treinado em: **500.000 horas de Ã¡udio limpo**
- VocabulÃ¡rio: 704 tokens (inglÃªs) / 2.454 tokens (multilingual)

**S3Gen â€” Token-to-Audio:**
- Decoder: `CausalMaskedDiffWithXvec` (Flow Matching)
- Turbo: **1 passo** â€” viabiliza latÃªncia ultra-baixa
- English/MTL: 10 passos â€” maior qualidade/expressividade
- Vocoder final: HiFTGenerator â†’ 24 kHz

**VoiceEncoder:**
- Extrai embeddings de 256 dimensÃµes do Ã¡udio de referÃªncia
- Condiciona tanto T3 quanto S3Gen
- ReferÃªncia processada a 16 kHz (S3_SR)

---

## InstalaÃ§Ã£o

### Via pip (recomendado)

```bash
pip install chatterbox-tts
```

### A partir do cÃ³digo-fonte (para desenvolvimento)

```bash
# Criar ambiente isolado (Python 3.11 recomendado)
conda create -yn chatterbox python=3.11
conda activate chatterbox

git clone https://github.com/resemble-ai/chatterbox.git
cd chatterbox
pip install -e .
```

> **Nota:** As dependÃªncias estÃ£o fixadas no `pyproject.toml` para garantir consistÃªncia. Desenvolvido e testado em Python 3.11 no Debian 11.

### InstalaÃ§Ã£o em hardware Blackwell / CUDA 13.0 (GB10, RTX 50xx)

Para GPUs com compute capability â‰¥ 12.0 (Blackwell) usando CUDA 13.0:

```bash
conda create -yn chatterbox python=3.11
conda activate chatterbox

# torch com suporte CUDA 13.0 para ARM64/x86
pip install torch==2.10.0+cu130 torchaudio==2.10.0+cu130 \
    --index-url https://download.pytorch.org/whl/cu130

# Chatterbox sem sobrescrever torch
pip install -e . --no-deps

# DependÃªncias crÃ­ticas (versÃµes obrigatÃ³rias)
pip install transformers==4.46.3 safetensors==0.5.3 \
    diffusers==0.29.0 "numpy>=1.24.0,<1.26.0" \
    soundfile s3tokenizer resemble-perth
```

> **Aviso esperado:** PyTorch 2.10 reporta `UserWarning` sobre compute capability 12.1 vs mÃ¡ximo suportado 12.0. Apenas informativo â€” CUDA funciona normalmente.

---

## Uso

### Chatterbox-Turbo (InglÃªs, Alta Velocidade)

```python
import soundfile as sf
import torch
from chatterbox.tts_turbo import ChatterboxTurboTTS

# Carregar modelo
model = ChatterboxTurboTTS.from_pretrained(device="cuda")

# GeraÃ§Ã£o simples (voz padrÃ£o)
text = "Hello! Welcome to Chatterbox TTS, the fastest open-source voice synthesis."
wav = model.generate(text)

# Com tags paralingÃ¼Ã­sticas
text_expressivo = (
    "Hi there! [chuckle] Great to hear from you. "
    "Let me check that for you [cough] â€” just one moment!"
)
wav = model.generate(text_expressivo)

# Com clonagem de voz (arquivo de referÃªncia ~10s, mono, 24 kHz)
wav = model.generate(text, audio_prompt_path="sua_voz_referencia.wav")

# Salvar Ã¡udio
audio_np = wav.squeeze().cpu().numpy()
sf.write("saida.wav", audio_np, model.sr)  # sr = 24000
```

### Chatterbox English (500M, Controle Expressivo)

```python
import soundfile as sf
import torch
from chatterbox.tts import ChatterboxTTS

model = ChatterboxTTS.from_pretrained(device="cuda")

text = "This is a test of the Chatterbox English model with expressive controls."

# ParÃ¢metros de expressividade
# exaggeration: 0.0 (neutro) â†’ 1.0 (muito expressivo), padrÃ£o 0.5
# cfg_weight: controla aderÃªncia Ã  voz de referÃªncia, padrÃ£o 0.5
wav = model.generate(text, exaggeration=0.7, cfg_weight=0.3)

# Com voz clonada
wav = model.generate(text, audio_prompt_path="referencia.wav", exaggeration=0.5)

audio_np = wav.squeeze().cpu().numpy()
sf.write("saida_en.wav", audio_np, model.sr)
```

### Chatterbox-Multilingual (23 Idiomas)

```python
import soundfile as sf
import torch
from chatterbox.mtl_tts import ChatterboxMultilingualTTS

model = ChatterboxMultilingualTTS.from_pretrained(device="cuda")

# PortuguÃªs (PT)
texto_pt = "OlÃ¡! Este Ã© um teste do modelo Chatterbox Multilingual em portuguÃªs."
wav = model.generate(texto_pt, language_id="pt")

# FrancÃªs
texto_fr = "Bonjour! Voici un exemple en franÃ§ais avec le modÃ¨le multilingue."
wav_fr = model.generate(texto_fr, language_id="fr")

# Espanhol com clone de voz cross-language
texto_es = "Hola! Este es un ejemplo de clonaciÃ³n de voz entre idiomas."
wav_clone = model.generate(
    texto_es,
    language_id="es",
    audio_prompt_path="referencia_pt.wav"  # voz em PT, fala em ES
)

# Salvar
audio_np = wav.squeeze().cpu().numpy()
sf.write("saida_pt.wav", audio_np, model.sr)
```

---

## Tags ParalingÃ¼Ã­sticas (Turbo)

O modelo Turbo suporta inserÃ§Ã£o nativa de eventos de fala naturais diretamente no texto:

| Tag | Efeito |
|-----|--------|
| `[chuckle]` | Riso suave / risada leve |
| `[laugh]` | Gargalhada |
| `[cough]` | Tosse |
| `[sigh]` | Suspiro |
| `[gasp]` | Ofego / surpresa |

**Exemplo:**
```python
text = (
    "Sarah here from support [chuckle], how can I help you today? "
    "[cough] Sorry about that â€” let me pull up your account."
)
wav = model.generate(text, audio_prompt_path="agente_voz.wav")
```

---

## Idiomas Suportados (Multilingual)

Ãrabe (ar) â€¢ DinamarquÃªs (da) â€¢ AlemÃ£o (de) â€¢ Grego (el) â€¢ **InglÃªs (en)** â€¢ **Espanhol (es)** â€¢ FinlandÃªs (fi) â€¢ **FrancÃªs (fr)** â€¢ Hebraico (he) â€¢ Hindi (hi) â€¢ Italiano (it) â€¢ JaponÃªs (ja) â€¢ Coreano (ko) â€¢ Malaio (ms) â€¢ HolandÃªs (nl) â€¢ NorueguÃªs (no) â€¢ PolonÃªs (pl) â€¢ **PortuguÃªs (pt)** â€¢ Russo (ru) â€¢ Sueco (sv) â€¢ SuaÃ­li (sw) â€¢ Turco (tr) â€¢ ChinÃªs (zh)

> 23 idiomas no total. Clone de voz cross-language suportado: forneÃ§a referÃªncia em um idioma e gere em outro.

---

## Clonagem de Voz Zero-Shot

### Como funciona

1. ForneÃ§a um Ã¡udio de referÃªncia (mÃ­nimo **5 segundos**, ideal **10+ segundos**)
2. O `VoiceEncoder` extrai embedding de 256 dimensÃµes da voz
3. T3 e S3Gen sÃ£o condicionados pelo embedding â€” **nenhum treinamento necessÃ¡rio**
4. A voz clonada Ã© gerada em qualquer idioma suportado

### Requisitos do Ã¡udio de referÃªncia

| ParÃ¢metro | Recomendado |
|-----------|-------------|
| DuraÃ§Ã£o | 10s+ (mÃ­nimo 5s para Turbo) |
| Formato | WAV, mono |
| Sample rate | 16â€“24 kHz |
| Qualidade | Sem ruÃ­do de fundo, voz clara |
| ConteÃºdo | Fala contÃ­nua, sem mÃºsica |

### Extraindo referÃªncia de um vÃ­deo

```bash
# Extrair Ã¡udio de um MP4 (10 segundos, pular os 2 primeiros)
ffmpeg -i video.mp4 -vn -ac 1 -ar 24000 \
       -ss 2 -t 10 -c:a pcm_s16le referencia.wav
```

---

## ParÃ¢metros de Controle (English / Multilingual)

| ParÃ¢metro | PadrÃ£o | DescriÃ§Ã£o |
|-----------|--------|-----------|
| `exaggeration` | `0.5` | Intensidade expressiva. `0.7+` para fala dramÃ¡tica |
| `cfg_weight` | `0.5` | AderÃªncia Ã  voz de referÃªncia. `0.3` melhora ritmo para locutores rÃ¡pidos |
| `audio_prompt_path` | `None` | Caminho para arquivo WAV de referÃªncia de voz |
| `language_id` | â€”  | CÃ³digo do idioma (apenas Multilingual) ex: `"pt"`, `"en"`, `"fr"` |

**Dicas:**
- Para fala neutra e consistente: `exaggeration=0.5, cfg_weight=0.5`
- Para fala expressiva/dramÃ¡tica: `exaggeration=0.7, cfg_weight=0.3`
- Se referÃªncia tem ritmo rÃ¡pido: reduza `cfg_weight` para ~0.3

---

## Performance e Requisitos de Hardware

### Real-Time Factor (RTF) â€” Benchmark Oficial

| Plataforma | RTF | Contexto |
|-----------|:---:|----------|
| RTX 4090 (streaming) | **0,499** | Gera 2Ã— mais rÃ¡pido que o tempo real |
| ServiÃ§o comercial Resemble AI | â€” | LatÃªncia ao primeiro chunk **<200ms** |
| ImplementaÃ§Ã£o streaming (open-source) | â€” | ~472ms ao primeiro chunk |

> RTF < 1.0 = geraÃ§Ã£o em tempo real. RTF 0,499 = produz 2 segundos de Ã¡udio para cada 1 segundo de processamento.

### LatÃªncia medida (GB10 Blackwell, 128 GB VRAM unificada)

| Modelo | Carregamento | GeraÃ§Ã£o tÃ­pica | Ãudio gerado |
|--------|:------------:|:--------------:|:------------:|
| Turbo | 1.262s (cache) | **~2.7s** | ~7s de fala |
| Turbo (com clone) | â€” | ~2.9s | ~7s de fala |
| Multilingual | 749.8s (1Âª vez) | **~4.4s** (PT) | ~6.7s de fala |
| English (500M) | ~similar MTL | ~3-5s | ~6-8s de fala |

> Primeira execuÃ§Ã£o faz download dos modelos (~21 min para Turbo, ~similar para os 500M). ExecuÃ§Ãµes subsequentes usam cache local.

### Requisitos de VRAM

| Uso | VRAM MÃ­nima | Recomendado |
|-----|:-----------:|:-----------:|
| Turbo (350M) | **4â€“6 GB** | 8 GB |
| English/MTL (500M) | **8â€“12 GB** | 16 GB |
| ProduÃ§Ã£o (alta concorrÃªncia) | 16â€“24 GB | 32 GB+ |

### Plataformas suportadas
- **NVIDIA CUDA** (recomendado) â€” RTX 3060+ / A4000+ / GB10
- **Apple MPS** (M1/M2/M3)
- **CPU** (funcional, mas lento)
- **AMD ROCm** (via builds compatÃ­veis)

---

## Perth Watermarking â€” IA ResponsÃ¡vel

Todo Ã¡udio gerado pelo Chatterbox inclui automaticamente a **marca d'Ã¡gua neural Perth** da Resemble AI â€” imperceptÃ­vel ao ouvido humano, mas detectÃ¡vel por mÃ¡quina.

### CaracterÃ­sticas
- Sobrevive a compressÃ£o MP3 e ediÃ§Ã£o de Ã¡udio, reamostragem, re-encoding, adiÃ§Ã£o de ruÃ­do e time-stretching
- PrecisÃ£o de detecÃ§Ã£o prÃ³xima a 100%
- Dados codificados em regiÃµes inaudÃ­veis do espectro (mascaramento auditivo)
- Atende requisitos de regulaÃ§Ã£o de conteÃºdo IA
- DisponÃ­vel como ferramenta independente: [github.com/resemble-ai/perth](https://github.com/resemble-ai/perth)

> O CEO da Resemble AI, Zohaib Ahmed, prestou testemunho ao **Senado dos EUA** sobre a importÃ¢ncia de watermarking em Ã¡udio sintÃ©tico gerado por IA.

### Verificar marca d'Ã¡gua

```python
import perth
import librosa

audio, sr = librosa.load("audio_gerado.wav", sr=None)
watermarker = perth.PerthImplicitWatermarker()
watermark = watermarker.get_watermark(audio, sample_rate=sr)
print(f"Marca d'Ã¡gua: {watermark}")  # 0.0 = sem marca, 1.0 = marcado
```

---

## AvaliaÃ§Ãµes de Qualidade

O Chatterbox Turbo foi avaliado via **Podonos** â€” plataforma de avaliaÃ§Ã£o subjetiva reproduzÃ­vel de fala â€” em comparaÃ§Ãµes diretas:

| ComparaÃ§Ã£o | Resultado |
|-----------|-----------|
| Chatterbox Turbo vs **ElevenLabs Turbo v2.5** | [Ver relatÃ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-elevenlabs-turbo) |
| Chatterbox Turbo vs **Cartesia Sonic 3** | [Ver relatÃ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-cartesia-sonic3) |
| Chatterbox Turbo vs **VibeVoice 7B** | [Ver relatÃ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-vibevoice7b) |

> **63,75% dos usuÃ¡rios preferiram Chatterbox** ao ElevenLabs em testes cegos independentes.

---

## Casos de Uso

| Ãrea | AplicaÃ§Ã£o |
|------|-----------|
| **Voice Agents** | Atendimento ao cliente, assistentes virtuais, IVR |
| **Dublagem** | LocalizaÃ§Ã£o de conteÃºdo audiovisual em mÃºltiplos idiomas |
| **NarraÃ§Ã£o** | Audiobooks, podcasts, e-learning |
| **Games & NPCs** | Vozes procedurais com personalidade |
| **Acessibilidade** | Leitores de tela expressivos, TTS para deficientes visuais |
| **CriaÃ§Ã£o de ConteÃºdo** | VÃ­deos com narraÃ§Ã£o automÃ¡tica em voz clonada |
| **Agentes de IA** | LLMs com saÃ­da de voz em tempo real (sub-150ms) |

---

## ImplantaÃ§Ã£o e IntegraÃ§Ãµes

### Plataformas de Hospedagem
- [HuggingFace Spaces](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo)
- [RunPod](https://runpod.io)
- [Modal](https://modal.com)
- [Replicate](https://replicate.com)
- [Fal](https://fal.ai)

### Self-Hosted com API REST
```bash
# Usando devnen/Chatterbox-TTS-Server
# API compatÃ­vel com OpenAI, Web UI, processamento de audiobooks
git clone https://github.com/devnen/Chatterbox-TTS-Server
```

### VLLM Port (alta throughput)
```bash
# randombk/chatterbox-vllm
git clone https://github.com/randombk/chatterbox-vllm
```

### VersÃ£o ONNX (cross-platform, sem PyTorch)

O Turbo possui versÃ£o ONNX no HuggingFace, adequada para deployment em hardware sem CUDA:

```bash
# Modelo ONNX: ResembleAI/chatterbox-turbo-ONNX
# Suporta NVIDIA (CUDA), AMD (ROCm) e CPU
```

---

## Estrutura do RepositÃ³rio

```
chatterbox/
â”œâ”€â”€ src/chatterbox/
â”‚   â”œâ”€â”€ tts.py              # ChatterboxTTS (English 500M)
â”‚   â”œâ”€â”€ tts_turbo.py        # ChatterboxTurboTTS (350M)
â”‚   â”œâ”€â”€ mtl_tts.py          # ChatterboxMultilingualTTS (500M)
â”‚   â”œâ”€â”€ models/
â”‚   â”‚   â”œâ”€â”€ t3/             # Modelo T3 (LLM: GPT2 / Llama)
â”‚   â”‚   â”œâ”€â”€ s3gen/          # Decoder CFM + HiFiGAN
â”‚   â”‚   â””â”€â”€ voice_encoder/  # VoiceEncoder (embeddings 256-dim)
â”‚   â””â”€â”€ data/               # Processamento de Ã¡udio e texto
â”œâ”€â”€ example_tts.py          # Exemplos de uso TTS
â”œâ”€â”€ example_vc.py           # Exemplos de voice clone
â”œâ”€â”€ pyproject.toml          # DependÃªncias fixadas
â””â”€â”€ README.md               # Este arquivo
```

### RepositÃ³rios HuggingFace

| Modelo | RepositÃ³rio HF |
|--------|---------------|
| Turbo (350M) | `ResembleAI/chatterbox-turbo` |
| English (500M) | `ResembleAI/chatterbox` |
| Multilingual (500M) | `ResembleAI/chatterbox-multilingual` |

---

## Comunidade

- **Discord:** [Entrar no servidor](https://discord.gg/rJq9cRJBJ6)
- **Issues:** [GitHub Issues](https://github.com/resemble-ai/chatterbox/issues)
- **Demos ao vivo:** [Turbo](https://resemble-ai.github.io/chatterbox_turbo_demopage/) | [Multilingual](https://resemble-ai.github.io/chatterbox_demopage/)

---

## Agradecimentos

- [Podonos](https://podonos.com) â€” avaliaÃ§Ã£o subjetiva de fala reproduzÃ­vel
- [Cosyvoice](https://github.com/FunAudioLLM/CosyVoice)
- [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning)
- [HiFT-GAN](https://github.com/yl4579/HiFTNet)
- [Llama 3](https://github.com/meta-llama/llama3)
- [S3Tokenizer](https://github.com/xingchensong/S3Tokenizer)

---

## CitaÃ§Ã£o

Se vocÃª usar este modelo em pesquisa, por favor cite:

```bibtex
@misc{chatterboxtts2025,
  author       = {{Resemble AI}},
  title        = {{Chatterbox-TTS}},
  year         = {2025},
  howpublished = {\url{https://github.com/resemble-ai/chatterbox}},
  note         = {GitHub repository}
}
```

---

## LicenÃ§a e Aviso Legal

**LicenÃ§a MIT** â€” uso comercial e modificaÃ§Ã£o permitidos. Veja [LICENSE](LICENSE) para detalhes.

> Este modelo nÃ£o deve ser utilizado para criaÃ§Ã£o de deepfakes, fraudes, personificaÃ§Ã£o nÃ£o autorizada ou qualquer uso malicioso. Todo Ã¡udio gerado contÃ©m marca d'Ã¡gua Perth para rastreabilidade. Os desenvolvedores nÃ£o se responsabilizam por uso indevido.

---

Projeto adaptado da comunidade ARCKHÉ TDS - Marca Arckhe