# Response Format

Use this format for the final response after generating images.

## Image output

```text
张数规划：
推荐张数：{1 / N}
输出形式：{single image / image series}
理由：{why this count is enough}

图片：
{embedded image or image paths; count must match planned image count}
```

## Short output

Default to:

```text
张数规划：{count and reason, based on one expression point per image}
图片：{separate paths; path count must equal count}
```

## Rules

Do not print the concept card, storyboard, or full prompt unless the user asks after image generation. Do not answer with text-only concept explanation when this skill is invoked. Use the planning workflow internally, create the image-count plan first, then generate the image or image series.
