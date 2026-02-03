# KI-basierte Trading-Lösung – Leitfaden

## Zielbild
Eine Anwendung, die für ausgewählte Aktien Kauf- und Verkaufsempfehlungen liefert, indem sie aktuelle Kennzahlen, Preisdaten und ggf. Nachrichten in ein Modell einspeist, das klare, nachvollziehbare Signale generiert.

## 1) Datenbasis (Input-Schicht)
**Marktdaten**
- Kursdaten (OHLCV), Volumen, Bid/Ask-Spreads.
- Technische Indikatoren: z. B. RSI, MACD, Moving Averages.

**Fundamentaldaten**
- KGV, KBV, Umsatz-/Gewinnwachstum, Margen.
- Quartals-/Jahresberichte, Guidance.

**Makro & Sentiment (optional)**
- Zinsentscheidungen, Inflation, Indexbewegungen.
- Nachrichten-Sentiment (Headline/Artikel-Score).

> Wichtig: Klare Datenquellen definieren (API-Lizenz, Aktualität, Latenz).

## 2) Feature Engineering
- Zeitreihen-Features: Rolling Windows, Returns, Volatilität.
- Normalisierung/Skalierung pro Aktie.
- Kategorische Events: Earnings-Dates, Dividenden.

## 3) Modellansätze
**Baseline (empfohlen):**
- Regelbasierte Signale + klassische ML-Modelle (Random Forest, XGBoost).

**Fortgeschritten:**
- Sequenzmodelle (LSTM/Transformer) für Zeitreihen.
- Mehrere Modelle als Ensemble.

## 4) Signal-Design (Kauf/Verkauf)
- Definiere klare Output-Schwellen: z. B. „Buy“, „Hold“, „Sell“.
- Erkläre Regeln: z. B. Modellscore > 0,7 = Buy.
- Risikohinweis integrieren (kein Finanzrat).

## 5) Backtesting & Evaluation
- Zeitreihen-spezifisches Cross-Validation (Walk-Forward).
- Kennzahlen: Sharpe Ratio, Max Drawdown, Trefferquote.
- Vergleich zu Benchmarks (z. B. Buy-and-Hold).

## 6) Architektur (Vorschlag)
**Backend**
- Dateningestion (Cron/Queue), Feature Pipeline, Modellservice.
- Modellversionierung (z. B. MLflow).

**Frontend**
- Dashboard: Portfolio, Signale, Erklärung, Performance.

**Monitoring**
- Drift-Erkennung (Daten & Modell).
- Alarmierung bei starken Abweichungen.

## 7) Rechtliche Hinweise
- Keine Anlageberatung: klare Disclaimer.
- Datenschutz (falls Nutzerprofile/Portfolios gespeichert werden).

## 8) MVP-Vorschlag
1. Eine Datenquelle (z. B. tägliche Kurse).
2. Ein Modell (z. B. XGBoost) + 3–5 Features.
3. Einfache UI mit Signal und Confidence.

## Nächste Schritte
- Klären: Asset-Universum, Datenquellen, Update-Frequenz.
- MVP-Plan: Features, Modell, Backtest, UI-Skizze.

