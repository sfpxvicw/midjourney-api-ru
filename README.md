# Midjourney API (`midjourney`)

<!-- conv-kit:v1 -->

<p align="center">
  <img src="assets/badges/price.svg" alt="observed unit price"> <img src="assets/badges/billing.svg" alt="billing model"> <img src="assets/badges/compat.svg" alt="OpenAI-compatible endpoint">
</p>

<p align="center">
  <img src="assets/01-product-hero-perfume.jpg" width="820" alt="Sample render via the APIMart image API">
</p>

> **from $0.045 per image** on the APIMart route — одна OpenAI-совместимая конечная точка на `https://api.apimart.ai/v1`, ежемесячный тариф не нужен. *(данные на 2026-10-12)*

**[Получить API-ключ](https://go.apimart.ai/k-4a566f)** · **[Актуальные цены](https://go.apimart.ai/k-d2d849)** · **[Страница модели](https://go.apimart.ai/k-eba47d)** · [⚡ Быстрый старт за 60 секунд](#quickstart)

**Почему команды используют Midjourney (`midjourney`) через APIMart**

- **Один ключ — весь каталог.** Тот же base URL `https://api.apimart.ai/v1` и тот же заголовок `Authorization` дают доступ к Midjourney (`midjourney`) и ещё 300+ моделям для изображений, видео и языка — менять нужно поле `model`, а не клиент.
- **Минимум $1, оплата по факту.** Ни подписки, ни предоплаченного тарифа, который нужно заранее рассчитать: пополняйте от $1 и расходуйте на вызовы.
- **Сумма списания возвращается в ответе.** Каждая завершённая задача сообщает списанную сумму (`cost` / `credits_cost`); задача со статусом `failed` возвращается на баланс.
- **Асинхронность по умолчанию.** Отправьте задачу, получите `task_id`, опрашивайте `GET /v1/tasks/{id}` — пакетная обработка и повторы это обычная работа с очередью, а не отдельная интеграция.

<!-- /conv-kit:v1 -->

**Также известен как:** Миджорни · Мидджорни

Midjourney is the industry-leading text-to-image engine, prized for its painterly aesthetic, strong composition, and signature lighting. APIMart exposes Midjourney as a programmable API — call /v1/midjourney/generations for the default Imagine flow, choose v8.1, v7, v6.1, v5.2, v5.1 or Niji 7 / Niji 6, dial in stylize / chaos / weird, and run on relax, fast, or turbo queues without touching Discord.

## Model id and routes

| Route | `model` value | Billing | Notes |
| --- | --- | --- | --- |
| Per-image | `midjourney` | per delivered image, by resolution | see the [model page](https://go.apimart.ai/k-eba47d) for the exact tiers |

Endpoint: `POST https://api.apimart.ai/v1/images/generations`, then poll `GET /v1/tasks/{task_id}`.

## Pricing

<!-- pricing:model:start -->
| Output | List price | Effective price |
| --- | --- | --- |
| default | 0.0563 | 0.04504 |
| blend | 0.0688 | 0.05504 |
| blend-fast | 0.0688 | 0.05504 |
| blend-turbo | 0.125 | 0.1 |
| describe | 0.0688 | 0.05504 |
| describe-fast | 0.0688 | 0.05504 |
| describe-turbo | 0.125 | 0.1 |
| edits | 0.0688 | 0.05504 |
| edits-fast | 0.0688 | 0.05504 |
| edits-turbo | 0.125 | 0.1 |
| high_variation | 0.0688 | 0.05504 |
| high_variation-fast | 0.0688 | 0.05504 |
| high_variation-turbo | 0.125 | 0.1 |
| imagine | 0.0563 | 0.04504 |
| imagine-fast | 0.0688 | 0.05504 |
| imagine-niji6 | 0.0563 | 0.04504 |
| imagine-niji6-fast | 0.0688 | 0.05504 |
| imagine-niji6-turbo | 0.125 | 0.1 |
| imagine-niji7 | 0.0563 | 0.04504 |
| imagine-niji7-fast | 0.0688 | 0.05504 |
| imagine-niji7-turbo | 0.125 | 0.1 |
| imagine-turbo | 0.125 | 0.1 |
| imagine-v5.1 | 0.0563 | 0.04504 |
| imagine-v5.1-fast | 0.0688 | 0.05504 |
| imagine-v5.1-turbo | 0.125 | 0.1 |
| imagine-v5.2 | 0.0563 | 0.04504 |
| imagine-v5.2-fast | 0.0688 | 0.05504 |
| imagine-v5.2-turbo | 0.125 | 0.1 |
| imagine-v6.1 | 0.0563 | 0.04504 |
| imagine-v6.1-fast | 0.0688 | 0.05504 |
| imagine-v6.1-turbo | 0.125 | 0.1 |
| imagine-v7 | 0.0563 | 0.04504 |
| imagine-v7-fast | 0.0688 | 0.05504 |
| imagine-v7-turbo | 0.125 | 0.1 |
| imagine-v8.1 | 0.0563 | 0.04504 |
| imagine-v8.1-fast | 0.0688 | 0.05504 |
| imagine-v8.1-turbo | 0.125 | 0.1 |
| imagine-v8.2 | 0.0563 | 0.04504 |
| imagine-v8.2-fast | 0.0688 | 0.05504 |
| imagine-v8.2-turbo | 0.125 | 0.1 |
| inpaint | 0.0688 | 0.05504 |
| inpaint-fast | 0.0688 | 0.05504 |
| inpaint-turbo | 0.125 | 0.1 |
| low_variation | 0.0688 | 0.05504 |
| low_variation-fast | 0.0688 | 0.05504 |
| low_variation-turbo | 0.125 | 0.1 |
| modal | 0.0688 | 0.05504 |
| modal-fast | 0.0688 | 0.05504 |
| modal-turbo | 0.125 | 0.1 |
| pan | 0.0688 | 0.05504 |
| pan-fast | 0.0688 | 0.05504 |
| pan-turbo | 0.125 | 0.1 |
| remix_strong | 0.0688 | 0.05504 |
| remix_strong-fast | 0.0688 | 0.05504 |
| remix_strong-turbo | 0.125 | 0.1 |
| remix_subtle | 0.0688 | 0.05504 |
| remix_subtle-fast | 0.0688 | 0.05504 |
| remix_subtle-turbo | 0.125 | 0.1 |
| reroll | 0.0688 | 0.05504 |
| reroll-fast | 0.0688 | 0.05504 |
| reroll-turbo | 0.125 | 0.1 |
| shorten | 0.0688 | 0.05504 |
| shorten-fast | 0.0688 | 0.05504 |
| shorten-turbo | 0.125 | 0.1 |
| upscale-hd | 0.0688 | 0.05504 |
| upscale-hd-fast | 0.0688 | 0.05504 |
| upscale-hd-turbo | 0.125 | 0.1 |
| variation | 0.0688 | 0.05504 |
| variation-fast | 0.0688 | 0.05504 |
| variation-turbo | 0.125 | 0.1 |
| video | 0.25 | 0.2 |
| video-720p | 0.5 | 0.4 |
| zoom | 0.0688 | 0.05504 |
| zoom-fast | 0.0688 | 0.05504 |
| zoom-turbo | 0.125 | 0.1 |


<!-- pricing:model:end -->

Prices are a snapshot; the [pricing page](https://go.apimart.ai/k-d2d849) and [`data/model.json`](data/model.json) are refreshed by CI, and a completed task reports the exact amount in its `cost` field.

## Request parameters

| Field | Type | Default | Notes |
| --- | --- | --- | --- |
| `model` | string | required | the model id shown in the route table above |
| `prompt` | string | required | what to generate, or what to change when editing |
| `size` | string | `auto` / `1:1` | aspect ratio, or `auto` where the route supports it |
| `resolution` | string | `1K` | output resolution tier — cost scales with it |
| `n` | integer | `1` | number of images per task, where the route allows more than one |
| `image_urls` | string[] | — | reference images as public HTTP(S) URLs or base64 data URLs |
| `nsfw_check` | boolean | `false` | runs `omni-moderation-latest` before submitting |

The table lists the fields accepted by the APIMart `images/generations` endpoint. Check the [model page](https://go.apimart.ai/k-eba47d) for anything this model adds on top.

## Quickstart

```bash
curl --request POST --url https://api.apimart.ai/v1/images/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  -d '{"model":"midjourney","prompt":"A bamboo forest at sunrise, slow push-in","size":"1:1","resolution":"1K"}'
```

```python
import os, time, requests

BASE = "https://api.apimart.ai/v1"
HEADERS = {"Authorization": f"Bearer {os.environ['APIMART_API_KEY']}", "Content-Type": "application/json"}

created = requests.post(f"{BASE}/images/generations", headers=HEADERS, timeout=60, json={
    "model": "midjourney", "prompt": "A bamboo forest at sunrise, slow push-in",
}).json()
task_id = created["data"]["id"]

while True:
    task = requests.get(f"{BASE}/tasks/{task_id}", headers=HEADERS, timeout=60).json()["data"]
    if task["status"] in ("completed", "failed"):
        break
    time.sleep(5)
print(task.get("cost"), task["result"]["images"][0]["url"])
```

Runnable versions: [`examples/`](examples). The task lifecycle is `pending → processing → completed | failed`.

## FAQ

**Какой id у модели Midjourney?**

`midjourney`. Смотрите таблицу маршрутов выше.

**Как тарифицируется?**

**from $0.045 per image** on the APIMart route. Завершённая задача указывает точную сумму в поле `cost`; неудачная задача возвращается на баланс.

**How do I get a key?**

Use the [Get an API key](https://go.apimart.ai/k-4a566f) link — $1 minimum top-up, no plan required.

## Attributed links (how this repository is measured)

| Purpose | Attributed link | Target |
| --- | --- | --- |
| Model page | <https://go.apimart.ai/k-eba47d> | `apimart.ai/ru/model/midjourney` |
| Live pricing | <https://go.apimart.ai/k-d2d849> | `apimart.ai/ru/pricing` |
| Get an API key | <https://go.apimart.ai/k-4a566f> | `apimart.ai/ru/keys` |

Outbound APIMart links are minted through the promo link API; hand-made tracking parameters are rejected by
`tools/check_links.py` in CI.

## Disclosure

Midjourney is a third-party model served through APIMart; this repository documents how to call it and publishes
model ids and prices, and does not claim official status. Model names, prices and documentation belong to their
respective owners.

## License

MIT — see [LICENSE](LICENSE).
