![Chatterbox Turbo Image](./Chatterbox-Turbo.jpg)

# Chatterbox TTS

[![Ouvir demos](https://img.shields.io/badge/ouvir-demos_de_êÂ¡udio-blue)](https://resemble-ai.github.io/chatterbox_turbo_demopage/)
[![HuggingFace Spaces](https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-sm.svg)](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo)
[![AvaliaêÂ§êÂ£o Podonos](https://static-public.podonos.com/badges/insight-on-pdns-sm-dark.svg)](https://podonos.com/resembleai/chatterbox)
[![Discord](https://img.shields.io/discord/1377773249798344776?label=entrar%20no%20discord&logo=discord&style=flat)](https://discord.gg/rJq9cRJBJ6)
[![LicenêÂ§a MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-green)](LICENSE)
[![Downloads HF](https://img.shields.io/badge/downloads-1M%2B-orange)](https://huggingface.co/ResembleAI)
[![GitHub Stars](https://img.shields.io/github/stars/resemble-ai/chatterbox?style=flat&label=stars)](https://github.com/resemble-ai/chatterbox)

_Desenvolvido com ê¢â¢Â¥ê¯Â¸Â por <a href="https://resemble.ai" target="_blank"><img width="100" alt="resemble-logo" src="https://github.com/user-attachments/assets/35cf756b-3506-4943-9c72-c05ddfa4e525" /></a>_

---

## O que êÂ© o Chatterbox?

**Chatterbox** êÂ© uma famêÂ­lia de trêÂªs modelos de sêÂ­ntese de voz (TTS) de cêÂ³digo aberto, estado da arte, desenvolvidos pela **Resemble AI**. LanêÂ§ado sob licenêÂ§a **MIT** (uso comercial livre), o Chatterbox ultrapassou **1 milhêÂ£o de downloads** no HuggingFace e superou soluêÂ§êÂµes comerciais como ElevenLabs em testes cegos ê¢â¬â com **63,75% de preferêÂªncia dos usuêÂ¡rios**.

### HistêÂ³rico de LanêÂ§amentos

| Data | Evento |
|------|--------|
| **Maio 2025** | LanêÂ§amento do **Chatterbox** original (500M, inglêÂªs, MIT) ê¢â¬â primeiro TTS open-source com controle de exageraêÂ§êÂ£o emocional. Atingiu 11.000+ estrelas no GitHub em poucas semanas |
| **Setembro 2025** | LanêÂ§amento do **Chatterbox-Multilingual** (500M, 23 idiomas) |
| **Dezembro 2025** | LanêÂ§amento do **Chatterbox-Turbo** (350M, inglêÂªs) ê¢â¬â avaliaêÂ§êÂ£o Podonos publicada em 12/12/2025. Superou ElevenLabs em 63,75% de preferêÂªncia |

### Por que escolher o Chatterbox?

| CritêÂ©rio | Chatterbox | ElevenLabs / Cartesia |
|----------|-----------|----------------------|
| LicenêÂ§a | **MIT (gratuito e comercial)** | ProprietêÂ¡rio (pago) |
| Voice Clone | **Zero-shot, sem treinamento** | Requer conta paga |
| Qualidade | **Avaliado superior em testes cegos** | ReferêÂªncia de mercado |
| Self-hosted | **Sim, 100% offline** | NêÂ£o |
| Watermark IA | **Sim (Perth, imperceptêÂ­vel)** | NêÂ£o |
| Idiomas | **23 idiomas (modelo MTL)** | Varia por plano |

---

## FamêÂ­lia de Modelos

<img width="1200" height="600" alt="Podonos Turbo Eval" src="https://storage.googleapis.com/chatterbox-demo-samples/turbo/podonos_turbo.png" />

### ê¢Å¡Â¡ Comparativo dos Modelos

| Modelo | ParêÂ¢metros | Idiomas | Destaques | Melhor Para | Demo | Exemplos |
|:-------|:----------:|:-------:|:----------|:------------|:----:|:--------:|
| **Chatterbox-Turbo** | **350M** | **InglêÂªs** | Tags paralingêÂ¼êÂ­sticas, 1-step decoder, menor VRAM | Voice agents em tempo real, produêÂ§êÂ£o | [Demo](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo) | [Ouvir](https://resemble-ai.github.io/chatterbox_turbo_demopage/) |
| **Chatterbox-Multilingual** | 500M | **23 idiomas** | Zero-shot cloning cross-language, backbone Llama | LocalizaêÂ§êÂ£o, dublagem, aplicaêÂ§êÂµes globais | [Demo](https://huggingface.co/spaces/ResembleAI/Chatterbox-Multilingual-TTS) | [Ouvir](https://resemble-ai.github.io/chatterbox_demopage/) |
| **Chatterbox** (English) | 500M | InglêÂªs | Controles CFG e Exaggeration, backbone Llama | TTS criativo, controle expressivo fino | [Demo](https://huggingface.co/spaces/ResembleAI/Chatterbox) | [Ouvir](https://resemble-ai.github.io/chatterbox_demopage/) |

---

## Arquitetura TêÂ©cnica

O pipeline segue dois estêÂ¡gios principais:

```
Texto + Embedding de Voz (256-dim)
         ê¢ââ
         ê¢âÂ¼
ê¢âÅê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âÂ
ê¢ââ   T3 (LLM)          ê¢ââ  GPT2 (Turbo) ou Llama (English/MTL)
ê¢ââ   Texto ê¢â â Tokens    ê¢ââ  VocabulêÂ¡rio: 704 (EN) / 2454 (MTL)
ê¢ââ   de Fala @ 25 Hz   ê¢ââ
ê¢ââê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âË
         ê¢ââ
         ê¢âÂ¼
ê¢âÅê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âÂ
ê¢ââ   S3Gen (CFM)        ê¢ââ  Flow Matching (Diffusion)
ê¢ââ   Tokens ê¢â â Mel       ê¢ââ  1 step (Turbo) ou 10 steps (outros)
ê¢ââ   Spectrograma       ê¢ââ  Entrada: S3_SR = 16.000 Hz
ê¢ââê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âË
         ê¢ââ
         ê¢âÂ¼
ê¢âÅê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âÂ
ê¢ââ   HiFiGAN Vocoder   ê¢ââ  Mel ê¢â â êÂudio WAV
ê¢ââ   SaêÂ­da @ 24 kHz    ê¢ââ  S3GEN_SR = 24.000 Hz
ê¢ââê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âË
         ê¢ââ
         ê¢âÂ¼
ê¢âÅê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âÂ
ê¢ââ   Perth Watermark   ê¢ââ  Marca d'êÂ¡gua neural imperceptêÂ­vel
ê¢ââê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢ââ¬ê¢âË
```

### Detalhes por Componente

**T3 ê¢â¬â Text-to-Speech-Token:**
- Backbone: GPT2 (Turbo / 350M) ou Llama (English & MTL / 500M)
- Taxa de saêÂ­da: 25 Hz de tokens de fala
- Condicionado por: tokens de texto + embedding de locutor (256 dims)
- Treinado em: **500.000 horas de êÂ¡udio limpo**
- VocabulêÂ¡rio: 704 tokens (inglêÂªs) / 2.454 tokens (multilingual)

**S3Gen ê¢â¬â Token-to-Audio:**
- Decoder: `CausalMaskedDiffWithXvec` (Flow Matching)
- Turbo: **1 passo** ê¢â¬â viabiliza latêÂªncia ultra-baixa
- English/MTL: 10 passos ê¢â¬â maior qualidade/expressividade
- Vocoder final: HiFTGenerator ê¢â â 24 kHz

**VoiceEncoder:**
- Extrai embeddings de 256 dimensêÂµes do êÂ¡udio de referêÂªncia
- Condiciona tanto T3 quanto S3Gen
- ReferêÂªncia processada a 16 kHz (S3_SR)

---

## InstalaêÂ§êÂ£o

### Via pip (recomendado)

```bash
pip install chatterbox-tts
```

### A partir do cêÂ³digo-fonte (para desenvolvimento)

```bash
# Criar ambiente isolado (Python 3.11 recomendado)
conda create -yn chatterbox python=3.11
conda activate chatterbox

git clone https://github.com/resemble-ai/chatterbox.git
cd chatterbox
pip install -e .
```

> **Nota:** As dependêÂªncias estêÂ£o fixadas no `pyproject.toml` para garantir consistêÂªncia. Desenvolvido e testado em Python 3.11 no Debian 11.

### InstalaêÂ§êÂ£o em hardware Blackwell / CUDA 13.0 (GB10, RTX 50xx)

Para GPUs com compute capability ê¢â°Â¥ 12.0 (Blackwell) usando CUDA 13.0:

```bash
conda create -yn chatterbox python=3.11
conda activate chatterbox

# torch com suporte CUDA 13.0 para ARM64/x86
pip install torch==2.10.0+cu130 torchaudio==2.10.0+cu130 \
    --index-url https://download.pytorch.org/whl/cu130

# Chatterbox sem sobrescrever torch
pip install -e . --no-deps

# DependêÂªncias crêÂ­ticas (versêÂµes obrigatêÂ³rias)
pip install transformers==4.46.3 safetensors==0.5.3 \
    diffusers==0.29.0 "numpy>=1.24.0,<1.26.0" \
    soundfile s3tokenizer resemble-perth
```

> **Aviso esperado:** PyTorch 2.10 reporta `UserWarning` sobre compute capability 12.1 vs mêÂ¡ximo suportado 12.0. Apenas informativo ê¢â¬â CUDA funciona normalmente.

---

## Uso

### Chatterbox-Turbo (InglêÂªs, Alta Velocidade)

```python
import soundfile as sf
import torch
from chatterbox.tts_turbo import ChatterboxTurboTTS

# Carregar modelo
model = ChatterboxTurboTTS.from_pretrained(device="cuda")

# GeraêÂ§êÂ£o simples (voz padrêÂ£o)
text = "Hello! Welcome to Chatterbox TTS, the fastest open-source voice synthesis."
wav = model.generate(text)

# Com tags paralingêÂ¼êÂ­sticas
text_expressivo = (
    "Hi there! [chuckle] Great to hear from you. "
    "Let me check that for you [cough] ê¢â¬â just one moment!"
)
wav = model.generate(text_expressivo)

# Com clonagem de voz (arquivo de referêÂªncia ~10s, mono, 24 kHz)
wav = model.generate(text, audio_prompt_path="sua_voz_referencia.wav")

# Salvar êÂ¡udio
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

# ParêÂ¢metros de expressividade
# exaggeration: 0.0 (neutro) ê¢â â 1.0 (muito expressivo), padrêÂ£o 0.5
# cfg_weight: controla aderêÂªncia êÂ  voz de referêÂªncia, padrêÂ£o 0.5
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

# PortuguêÂªs (PT)
texto_pt = "OlêÂ¡! Este êÂ© um teste do modelo Chatterbox Multilingual em portuguêÂªs."
wav = model.generate(texto_pt, language_id="pt")

# FrancêÂªs
texto_fr = "Bonjour! Voici un exemple en franêÂ§ais avec le modêÂ¨le multilingue."
wav_fr = model.generate(texto_fr, language_id="fr")

# Espanhol com clone de voz cross-language
texto_es = "Hola! Este es un ejemplo de clonaciêÂ³n de voz entre idiomas."
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

## Tags ParalingêÂ¼êÂ­sticas (Turbo)

O modelo Turbo suporta inserêÂ§êÂ£o nativa de eventos de fala naturais diretamente no texto:

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
    "[cough] Sorry about that ê¢â¬â let me pull up your account."
)
wav = model.generate(text, audio_prompt_path="agente_voz.wav")
```

---

## Idiomas Suportados (Multilingual)

êÂrabe (ar) ê¢â¬Â¢ DinamarquêÂªs (da) ê¢â¬Â¢ AlemêÂ£o (de) ê¢â¬Â¢ Grego (el) ê¢â¬Â¢ **InglêÂªs (en)** ê¢â¬Â¢ **Espanhol (es)** ê¢â¬Â¢ FinlandêÂªs (fi) ê¢â¬Â¢ **FrancêÂªs (fr)** ê¢â¬Â¢ Hebraico (he) ê¢â¬Â¢ Hindi (hi) ê¢â¬Â¢ Italiano (it) ê¢â¬Â¢ JaponêÂªs (ja) ê¢â¬Â¢ Coreano (ko) ê¢â¬Â¢ Malaio (ms) ê¢â¬Â¢ HolandêÂªs (nl) ê¢â¬Â¢ NorueguêÂªs (no) ê¢â¬Â¢ PolonêÂªs (pl) ê¢â¬Â¢ **PortuguêÂªs (pt)** ê¢â¬Â¢ Russo (ru) ê¢â¬Â¢ Sueco (sv) ê¢â¬Â¢ SuaêÂ­li (sw) ê¢â¬Â¢ Turco (tr) ê¢â¬Â¢ ChinêÂªs (zh)

> 23 idiomas no total. Clone de voz cross-language suportado: forneêÂ§a referêÂªncia em um idioma e gere em outro.

---

## Clonagem de Voz Zero-Shot

### Como funciona

1. ForneêÂ§a um êÂ¡udio de referêÂªncia (mêÂ­nimo **5 segundos**, ideal **10+ segundos**)
2. O `VoiceEncoder` extrai embedding de 256 dimensêÂµes da voz
3. T3 e S3Gen sêÂ£o condicionados pelo embedding ê¢â¬â **nenhum treinamento necessêÂ¡rio**
4. A voz clonada êÂ© gerada em qualquer idioma suportado

### Requisitos do êÂ¡udio de referêÂªncia

| ParêÂ¢metro | Recomendado |
|-----------|-------------|
| DuraêÂ§êÂ£o | 10s+ (mêÂ­nimo 5s para Turbo) |
| Formato | WAV, mono |
| Sample rate | 16ê¢â¬â24 kHz |
| Qualidade | Sem ruêÂ­do de fundo, voz clara |
| ConteêÂºdo | Fala contêÂ­nua, sem mêÂºsica |

### Extraindo referêÂªncia de um vêÂ­deo

```bash
# Extrair êÂ¡udio de um MP4 (10 segundos, pular os 2 primeiros)
ffmpeg -i video.mp4 -vn -ac 1 -ar 24000 \
       -ss 2 -t 10 -c:a pcm_s16le referencia.wav
```

---

## ParêÂ¢metros de Controle (English / Multilingual)

| ParêÂ¢metro | PadrêÂ£o | DescriêÂ§êÂ£o |
|-----------|--------|-----------|
| `exaggeration` | `0.5` | Intensidade expressiva. `0.7+` para fala dramêÂ¡tica |
| `cfg_weight` | `0.5` | AderêÂªncia êÂ  voz de referêÂªncia. `0.3` melhora ritmo para locutores rêÂ¡pidos |
| `audio_prompt_path` | `None` | Caminho para arquivo WAV de referêÂªncia de voz |
| `language_id` | ê¢â¬â  | CêÂ³digo do idioma (apenas Multilingual) ex: `"pt"`, `"en"`, `"fr"` |

**Dicas:**
- Para fala neutra e consistente: `exaggeration=0.5, cfg_weight=0.5`
- Para fala expressiva/dramêÂ¡tica: `exaggeration=0.7, cfg_weight=0.3`
- Se referêÂªncia tem ritmo rêÂ¡pido: reduza `cfg_weight` para ~0.3

---

## Performance e Requisitos de Hardware

### Real-Time Factor (RTF) ê¢â¬â Benchmark Oficial

| Plataforma | RTF | Contexto |
|-----------|:---:|----------|
| RTX 4090 (streaming) | **0,499** | Gera 2êâ mais rêÂ¡pido que o tempo real |
| ServiêÂ§o comercial Resemble AI | ê¢â¬â | LatêÂªncia ao primeiro chunk **<200ms** |
| ImplementaêÂ§êÂ£o streaming (open-source) | ê¢â¬â | ~472ms ao primeiro chunk |

> RTF < 1.0 = geraêÂ§êÂ£o em tempo real. RTF 0,499 = produz 2 segundos de êÂ¡udio para cada 1 segundo de processamento.

### LatêÂªncia medida (GB10 Blackwell, 128 GB VRAM unificada)

| Modelo | Carregamento | GeraêÂ§êÂ£o têÂ­pica | êÂudio gerado |
|--------|:------------:|:--------------:|:------------:|
| Turbo | 1.262s (cache) | **~2.7s** | ~7s de fala |
| Turbo (com clone) | ê¢â¬â | ~2.9s | ~7s de fala |
| Multilingual | 749.8s (1êÂª vez) | **~4.4s** (PT) | ~6.7s de fala |
| English (500M) | ~similar MTL | ~3-5s | ~6-8s de fala |

> Primeira execuêÂ§êÂ£o faz download dos modelos (~21 min para Turbo, ~similar para os 500M). ExecuêÂ§êÂµes subsequentes usam cache local.

### Requisitos de VRAM

| Uso | VRAM MêÂ­nima | Recomendado |
|-----|:-----------:|:-----------:|
| Turbo (350M) | **4ê¢â¬â6 GB** | 8 GB |
| English/MTL (500M) | **8ê¢â¬â12 GB** | 16 GB |
| ProduêÂ§êÂ£o (alta concorrêÂªncia) | 16ê¢â¬â24 GB | 32 GB+ |

### Plataformas suportadas
- **NVIDIA CUDA** (recomendado) ê¢â¬â RTX 3060+ / A4000+ / GB10
- **Apple MPS** (M1/M2/M3)
- **CPU** (funcional, mas lento)
- **AMD ROCm** (via builds compatêÂ­veis)

---

## Perth Watermarking ê¢â¬â IA ResponsêÂ¡vel

Todo êÂ¡udio gerado pelo Chatterbox inclui automaticamente a **marca d'êÂ¡gua neural Perth** da Resemble AI ê¢â¬â imperceptêÂ­vel ao ouvido humano, mas detectêÂ¡vel por mêÂ¡quina.

### CaracterêÂ­sticas
- Sobrevive a compressêÂ£o MP3 e ediêÂ§êÂ£o de êÂ¡udio, reamostragem, re-encoding, adiêÂ§êÂ£o de ruêÂ­do e time-stretching
- PrecisêÂ£o de detecêÂ§êÂ£o prêÂ³xima a 100%
- Dados codificados em regiêÂµes inaudêÂ­veis do espectro (mascaramento auditivo)
- Atende requisitos de regulaêÂ§êÂ£o de conteêÂºdo IA
- DisponêÂ­vel como ferramenta independente: [github.com/resemble-ai/perth](https://github.com/resemble-ai/perth)

> O CEO da Resemble AI, Zohaib Ahmed, prestou testemunho ao **Senado dos EUA** sobre a importêÂ¢ncia de watermarking em êÂ¡udio sintêÂ©tico gerado por IA.

### Verificar marca d'êÂ¡gua

```python
import perth
import librosa

audio, sr = librosa.load("audio_gerado.wav", sr=None)
watermarker = perth.PerthImplicitWatermarker()
watermark = watermarker.get_watermark(audio, sample_rate=sr)
print(f"Marca d'êÂ¡gua: {watermark}")  # 0.0 = sem marca, 1.0 = marcado
```

---

## AvaliaêÂ§êÂµes de Qualidade

O Chatterbox Turbo foi avaliado via **Podonos** ê¢â¬â plataforma de avaliaêÂ§êÂ£o subjetiva reproduzêÂ­vel de fala ê¢â¬â em comparaêÂ§êÂµes diretas:

| ComparaêÂ§êÂ£o | Resultado |
|-----------|-----------|
| Chatterbox Turbo vs **ElevenLabs Turbo v2.5** | [Ver relatêÂ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-elevenlabs-turbo) |
| Chatterbox Turbo vs **Cartesia Sonic 3** | [Ver relatêÂ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-cartesia-sonic3) |
| Chatterbox Turbo vs **VibeVoice 7B** | [Ver relatêÂ³rio](https://podonos.com/resembleai/chatterbox-turbo-vs-vibevoice7b) |

> **63,75% dos usuêÂ¡rios preferiram Chatterbox** ao ElevenLabs em testes cegos independentes.

---

## Casos de Uso

| êÂrea | AplicaêÂ§êÂ£o |
|------|-----------|
| **Voice Agents** | Atendimento ao cliente, assistentes virtuais, IVR |
| **Dublagem** | LocalizaêÂ§êÂ£o de conteêÂºdo audiovisual em mêÂºltiplos idiomas |
| **NarraêÂ§êÂ£o** | Audiobooks, podcasts, e-learning |
| **Games & NPCs** | Vozes procedurais com personalidade |
| **Acessibilidade** | Leitores de tela expressivos, TTS para deficientes visuais |
| **CriaêÂ§êÂ£o de ConteêÂºdo** | VêÂ­deos com narraêÂ§êÂ£o automêÂ¡tica em voz clonada |
| **Agentes de IA** | LLMs com saêÂ­da de voz em tempo real (sub-150ms) |

---

## ImplantaêÂ§êÂ£o e IntegraêÂ§êÂµes

### Plataformas de Hospedagem
- [HuggingFace Spaces](https://huggingface.co/spaces/ResembleAI/chatterbox-turbo-demo)
- [RunPod](https://runpod.io)
- [Modal](https://modal.com)
- [Replicate](https://replicate.com)
- [Fal](https://fal.ai)

### Self-Hosted com API REST
```bash
# Usando devnen/Chatterbox-TTS-Server
# API compatêÂ­vel com OpenAI, Web UI, processamento de audiobooks
git clone https://github.com/devnen/Chatterbox-TTS-Server
```

### VLLM Port (alta throughput)
```bash
# randombk/chatterbox-vllm
git clone https://github.com/randombk/chatterbox-vllm
```

### VersêÂ£o ONNX (cross-platform, sem PyTorch)

O Turbo possui versêÂ£o ONNX no HuggingFace, adequada para deployment em hardware sem CUDA:

```bash
# Modelo ONNX: ResembleAI/chatterbox-turbo-ONNX
# Suporta NVIDIA (CUDA), AMD (ROCm) e CPU
```

---

## Estrutura do RepositêÂ³rio

```
chatterbox/
ê¢âÅê¢ââ¬ê¢ââ¬ src/chatterbox/
ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ tts.py              # ChatterboxTTS (English 500M)
ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ tts_turbo.py        # ChatterboxTurboTTS (350M)
ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ mtl_tts.py          # ChatterboxMultilingualTTS (500M)
ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ models/
ê¢ââ   ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ t3/             # Modelo T3 (LLM: GPT2 / Llama)
ê¢ââ   ê¢ââ   ê¢âÅê¢ââ¬ê¢ââ¬ s3gen/          # Decoder CFM + HiFiGAN
ê¢ââ   ê¢ââ   ê¢ââê¢ââ¬ê¢ââ¬ voice_encoder/  # VoiceEncoder (embeddings 256-dim)
ê¢ââ   ê¢ââê¢ââ¬ê¢ââ¬ data/               # Processamento de êÂ¡udio e texto
ê¢âÅê¢ââ¬ê¢ââ¬ example_tts.py          # Exemplos de uso TTS
ê¢âÅê¢ââ¬ê¢ââ¬ example_vc.py           # Exemplos de voice clone
ê¢âÅê¢ââ¬ê¢ââ¬ pyproject.toml          # DependêÂªncias fixadas
ê¢ââê¢ââ¬ê¢ââ¬ README.md               # Este arquivo
```

### RepositêÂ³rios HuggingFace

| Modelo | RepositêÂ³rio HF |
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

- [Podonos](https://podonos.com) ê¢â¬â avaliaêÂ§êÂ£o subjetiva de fala reproduzêÂ­vel
- [Cosyvoice](https://github.com/FunAudioLLM/CosyVoice)
- [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning)
- [HiFT-GAN](https://github.com/yl4579/HiFTNet)
- [Llama 3](https://github.com/meta-llama/llama3)
- [S3Tokenizer](https://github.com/xingchensong/S3Tokenizer)

---

## CitaêÂ§êÂ£o

Se vocêÂª usar este modelo em pesquisa, por favor cite:

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

## LicenêÂ§a e Aviso Legal

**LicenêÂ§a MIT** ê¢â¬â uso comercial e modificaêÂ§êÂ£o permitidos. Veja [LICENSE](LICENSE) para detalhes.

> Este modelo nêÂ£o deve ser utilizado para criaêÂ§êÂ£o de deepfakes, fraudes, personificaêÂ§êÂ£o nêÂ£o autorizada ou qualquer uso malicioso. Todo êÂ¡udio gerado contêÂ©m marca d'êÂ¡gua Perth para rastreabilidade. Os desenvolvedores nêÂ£o se responsabilizam por uso indevido.

---

Projeto adaptado da comunidade ARCKHê TDS - ARCKHÉe