# RP-Preset
RP Preset

# RP-Preset

A tuned generation preset I created for local model Gemma 4 to at least (I hope) copy Claude style. I admit it will still have standard cliche like white knuckle, physical blow etc.
Use original preset for initial preset, Hemingway for shorter prose style, while BMC is experiment to cut as much token as possible. 
Currently my aim is to try make preset with more formula, but I'm not an programmer, so it's vibecode. 

### 📊 Token Weight Comparison

| Section | 1. Original Preset (OG) | 2. Black Magic (Hemingway) | 3. Black Magic (Claude Text) | 4. BMC Emoji | Total Saved (vs. OG) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`Directive` (System)** | ~835 tokens | ~310 tokens | ~342 tokens | **~214 tokens** | **~621 tokens** |
| **`CoT` (Thinking Block)** | ~142 tokens | ~78 tokens | ~81 tokens | **~54 tokens** | **~88 tokens** |
| **Total Preset Overhead** | **~977 tokens** | **~388 tokens** | **~423 tokens** | **~268 tokens** | **~709 tokens (-72.5%)** |

## 🎛️ Generation Parameters

---

### Core & Sampling Settings
| Parameter | Value | Description |
| :--- | :---: | :--- |
| **Temperature** | `1.0` | Balanced creativity and consistency. |
| **Max Tokens** | `4048` | Maximum length allowed for the model's response. |
| **Top P** | `0.95` | Discards the least likely 5% of tokens to maintain coherence. |
| **Top K** | `64` | Limits the pool to the top 64 most probable tokens. |
| **Min P** | `0.2` | Dynamic thresholding; filters out tokens below 20% of the top token's probability. |

### 🧠 Reasoning & Verbosity (CoT)
| Parameter | Value | Description |
| :--- | :---: | :--- |
| **Thinking** | `true` | Enables Chain-of-Thought (CoT) processing. |
| **Enable Thinking** | `true` | Forces the model to use internal reasoning. |
| **Reasoning Effort**| `high` | Allocates maximum computational weight to logical breakdown. |
| **Verbosity** | `low` | Keeps the final output concise and focused on the story action. |

### 🚫 Penalty & DRY Settings
| Parameter | Value | Description |
| :--- | :---: | :--- |
| **Frequency Penalty**| `1.05` | Slight penalty to discourage the repetition of identical words. |
| **Presence Penalty** | `0` | No structural penalty for introducing new topics. |
| **DRY Multiplier** | `0.8` | Don't Repeat Yourself multiplier to prevent phrase looping. |
| **DRY Base** | `1.8` | Exponential base for calculating the DRY repetition penalty. |

### 🔧 Adaptive & System Defaults
| Parameter | Value | Description |
| :--- | :---: | :--- |
| **Adaptive P Target**| `0.6` | Target probability for dynamic sample sizing. |
| **Adaptive P Decay** | `0.5` | Decay rate for the adaptive confidence window. |
| **Service Tier** | `null`| Uses default provider routing. |
| **Assistant Prefill**| `""` | No forced starting text for the assistant response. |

---

## 📄 Raw JSON Configuration

If you need to import this directly into your frontend or API client:

```json
{
  "chatParameters": {
    "temperature": 1,
    "maxTokens": 4096,
    "topP": 0.95,
    "topK": 64,
    "frequencyPenalty": 1.05,
    "presencePenalty": 0,
    "reasoningEffort": "high",
    "verbosity": "low",
    "serviceTier": null,
    "assistantPrefill": "",
    "customParameters": {
      "thinking": true,
      "enable_thinking": true,
      "min_p": 0.2,
      "adaptive_p_target": 0.6,
      "adaptive_p_decay": 0.5,
      "dry_multiplier": 0.8,
      "dry_base": 1.8
    }
  }
}
