# Данные проекта

В работе используются 54 отчёта AAPL, JNJ и CAT за период с 1 января 2021 года по 1 июня 2025 года, по 18 наблюдений на компанию.

| Файл | Содержимое |
|:---|:---|
| `master_dataset_v8.parquet` | Итоговые 54 наблюдения с текстами prepared remarks / Q&A, EPS surprise, датами и целевыми доходностями |
| `master_dataset_preview_v8.csv` | Тот же датасет без длинных текстов |
| `eps_surprises_v8.csv` | EPS estimate, EPS actual, surprise и признак публикации до открытия рынка |
| `prices_v8.parquet` | Цены для целевых доходностей, momentum и торговой интерпретации |
| `sentiment_cache_v8.csv` | Готовые оценки FinBERT для prepared remarks и Q&A |
| `transcripts/` | 54 исходных транскрипта с тикером, датой и финансовым кварталом |

Цены и EPS получены через Yahoo Finance / `yfinance`. Транскрипты взяты из [defeatbeta/yahoo-finance-data](https://huggingface.co/datasets/defeatbeta/yahoo-finance-data). Внешние источники не обновлялись при оформлении репозитория.

Sentiment cache сопоставляется с наблюдениями по порядку строк после сортировки по `earn_date`, как в исходном notebook. При изменении состава или порядка датасета кэш нужно пересобрать. `surprise_pct` и доходности хранятся в долях: `0.01` означает 1%.

Notebook использует относительный путь `data/`, поэтому Jupyter запускается из корня проекта.
