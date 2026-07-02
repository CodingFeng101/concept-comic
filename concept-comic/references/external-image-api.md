# External Image API

Use this when the skill runs outside Codex or any editor that lacks a native image generation tool.

## Required configuration

Read configuration from environment variables:

```text
OPENAI_API_KEY     required
OPENAI_BASE_URL    optional, default: https://api.openai.com/v1
OPENAI_IMAGE_MODEL optional, default: gpt-image-2
```

Use the Images API for direct generation:

```text
POST {OPENAI_BASE_URL}/images/generations
Authorization: Bearer {OPENAI_API_KEY}
Content-Type: application/json
```

Default payload:

```json
{
  "model": "gpt-image-2",
  "prompt": "{final concept-comic prompt}",
  "n": 1,
  "size": "2048x1152",
  "quality": "medium"
}
```

For image series, send one request per planned image with `n: 1`. Do not set `n` to the planned count and do not ask for the whole series in one prompt; the model may return one combined montage instead of separate concept-comic outputs.

## Curl pattern

```bash
curl -X POST "${OPENAI_BASE_URL:-https://api.openai.com/v1}/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "'"${OPENAI_IMAGE_MODEL:-gpt-image-2}"'",
    "prompt": "FINAL_PROMPT_HERE",
    "n": 1,
    "size": "2048x1152",
    "quality": "medium"
  }'
```

Decode `data[0].b64_json` and write it to a `.png` file. For multiple returned images, save each item in `data` separately.

## Python pattern

```python
import base64
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ["OPENAI_API_KEY"],
    base_url=os.environ.get("OPENAI_BASE_URL", "https://api.openai.com/v1"),
)

result = client.images.generate(
    model=os.environ.get("OPENAI_IMAGE_MODEL", "gpt-image-2"),
    prompt=final_prompt,
    n=1,
    size="2048x1152",
    quality="medium",
)

image_bytes = base64.b64decode(result.data[0].b64_json)
with open(output_path, "wb") as f:
    f.write(image_bytes)
```

## Failure handling

- If `OPENAI_API_KEY` is missing, stop and tell the user to configure it.
- If `OPENAI_BASE_URL` is present, use it exactly as configured after trimming a trailing slash.
- If the API rejects `gpt-image-2`, report the provider/model error instead of silently falling back.
- If moderation or organization verification blocks the request, report that blocker plainly.

Official reference: https://developers.openai.com/api/docs/guides/image-generation
