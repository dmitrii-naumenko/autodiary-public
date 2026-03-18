# Autodiary — Personal Analytics Platform

> Превращает разрозненные жизненные данные в понятные выводы и действия.
> Evidence-first: каждый вывод опирается на данные, а не на ощущения.

---

## Проблема

Трекеры генерируют море данных — пульс, сон, тренировки, дневник, рабочие сессии — но каждый живёт в своём силосе. Кросс-доменные связи (сон ↔ продуктивность ↔ здоровье) невидимы. 140+ метрик, ни одного вывода.

## Решение

```
Signals → Aggregates → Evidence → Insights → Actions
                    ↻ Continual Improvement (ITIL SVS)
```

Единая аналитическая платформа: собирает сигналы из 8+ источников, агрегирует в метрики, находит паттерны, формулирует инсайты с доказательной базой и предлагает конкретные действия. Замкнутый цикл — система учится на обратной связи.

---

## Архитектура

```
Sources (8+)                              Consumers
  Apple Health · Google Forms             ┌─ Claude Desktop (ad-hoc)
  AutoSleep · Session tracker             ├─ Claude Code Agents
       │                                  ├─ Grafana (10+ dashboards)
  Collector → Dataset Layer → Metric      └─ macOS Alerts
  Engine → PostgreSQL + pgvector →
  DataAPI / MCP Server ──────────────────→
```

**Config-driven:** добавление метрики = одна запись в YAML + один калькулятор.

---

## Ключевые возможности

🔬 **Evidence-first AI** — вывод без доказательной базы блокируется или маркируется как гипотеза

🔗 **Кросс-доменный анализ** — сон ↔ продуктивность ↔ здоровье ↔ тренировки в одной системе

🧠 **Живая память** — 51 инсайт, pgvector дедупликация, Merge & Enrich

🔄 **Feedback loop** — оценки инсайтов адаптируют критерии извлечения

🔒 **Privacy by design** — 3 профиля видимости, masked values, демо на реальных данных

🔌 **LLM-agnostic** — MCP контракт не зависит от модели

---

## Демо

<!-- Скриншоты в privacy mode -->

| Grafana: дашборд активности | Grafana: дашборд инсайтов |
|:--:|:--:|
| ![Activity](assets/dashboard_activity.png) | ![Insights](assets/dashboard_insights.png) |

| Claude Desktop: ad-hoc вопрос через MCP | MCP Server config |
|:--:|:--:|
| ![Chat](assets/demo_swimming.png) | ![MCP](assets/mcp_config.png) |

---

## Технологии

`Python 3.11` · `FastAPI` · `PostgreSQL + pgvector` · `Pydantic` · `Alembic` · `Docker Compose` · `Grafana` · `FastMCP` · `Claude Code` · `Google Drive API` · `pymorphy3`

## Система в числах

| Метрики | Домены | Источники | Данные | Инсайты | Дашборды |
|:-------:|:------:|:---------:|:------:|:-------:|:--------:|
| 140+ | 9 | 8+ | 800+ дней | 51 | 10+ |

---

## Документация

- [Видение и цели](docs/vision.md)
- [Методология](docs/methodology.md)
- [Продуктовая презентация (PDF)](presentation/autodiary_product.pdf)
- Техническая презентация — по запросу

---

## Контакт

Dmitrii Naumenko — [dmitrii@dsnaumenko.ru](mailto:dmitrii@dsnaumenko.ru) · [@naumenko_ds](https://t.me/naumenko_ds)

---

*Showcase-репозиторий. Исходный код — в приватном репо.*
