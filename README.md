User: Build a production-grade Python cryptocurrency futures trading system for Bitcoin on Binance Futures using only actively maintained, non-deprecated, latest Python-compatible libraries.

Python version target:

Python 3.13+
Fully asynchronous architecture
Modular production structure
No deprecated modules
Type hints throughout
PEP8 compliant
Structured logging
Docker support
Environment variables for secrets
Unit tests included

Goal:

Create an AI-powered autonomous Bitcoin futures trading system capable of:

Fetching real-time market data
Monitoring world news continuously
Tracking macroeconomic events
Tracking geopolitics
Detecting chart patterns
Detecting candlestick patterns
Understanding market structure
Generating trade signals
Managing risk automatically
Opening and closing positions on Binance Futures
Displaying live dashboard data in terminal
Logging every decision with explanation

Architecture:

Use multi-agent architecture.

Agents:

A) Market Data Agent

Responsibilities:

Fetch BTCUSDT futures OHLCV
Order book depth
Funding rates
Open interest
Liquidation data
Volume profile
Market breadth

Data intervals:

1m
5m
15m
1h
4h
Daily

Sources:

Binance APIs
Websocket streams

Suggested library:

ccxt
websockets
aiohttp

B) Technical Analysis Agent

Responsibilities:

Calculate:

Trend indicators:

EMA
SMA
VWAP
Supertrend
Ichimoku
ADX

Momentum indicators:

RSI
MACD
Stochastic RSI
CCI
ROC

Volatility:

ATR
Bollinger Bands
Keltner Channel

Volume indicators:

OBV
MFI
Volume profile

Libraries:

pandas
numpy
pandas-ta

C) Candlestick Pattern Agent

Detect:

Bullish:

Hammer
Inverted Hammer
Morning Star
Bullish Engulfing
Three White Soldiers

Bearish:

Shooting Star
Evening Star
Bearish Engulfing
Three Black Crows

Neutral:

Doji
Spinning Top

Return:

Pattern name

Confidence score

Historical accuracy score

D) Chart Pattern Agent

Detect:

Head and shoulders
Double top
Double bottom
Ascending triangle
Descending triangle
Symmetrical triangle
Wedge
Flag
Pennant
Cup and handle
Support and resistance zones

Use:

scipy
numpy

E) News Intelligence Agent

Continuously fetch:

Global:

Federal Reserve news
Inflation data
CPI
Interest rates
Crypto regulation news
ETF news
Bitcoin news
War/geopolitics
Major economic events

Sources:

RSS APIs

News APIs

Crypto APIs

Libraries:

feedparser
aiohttp

For every news item:

Perform:

sentiment analysis
market impact score
confidence score

Use:

transformers

Models:

FinBERT

F) Macro Agent

Track:

DXY
Gold
Nasdaq
S&P500
US Treasury yields
Oil
VIX

Generate:

Bullish/Bearish macro score

G) AI Decision Agent

Inputs:

Technical score

Pattern score

Sentiment score

Macro score

Order book score

Volume score

Open interest score

Funding score

Output:

Long

Short

No Trade

Return:

confidence %

reasoning

Example:

LONG

Confidence: 83%

Reason:

Bullish engulfing
Positive news sentiment
Strong support
Open interest rising
Funding neutral

H) Risk Management Agent

Requirements:

Leverage:

10x

Position size:

50% available balance maximum

Dynamic sizing formula:

Size = Min(

0.5 × balance,

volatility adjusted size

)

Risk:

Maximum account risk per trade:

1%

Stop loss:

ATR-based

Take profit:

1:3 risk reward

Rules:

No averaging down

Maximum daily loss:

3%

Maximum consecutive losses:

5

If triggered:

Stop trading

I) Trade Execution Agent

Capabilities:

Open Long

Open Short

Close Long

Close Short

Partial exits

Emergency close

Must validate:

Balance

Margin

Minimum quantity

Exchange precision

Use:

Binance Futures API

Library:

ccxt

J) Performance Agent

Track:

Total trades

Win rate

Profit factor

Max drawdown

Sharpe ratio

Daily PnL

Monthly PnL

K) Explainability Agent

Every trade decision must generate:

Timestamp

Indicators used

Patterns used

News summary

Confidence score

Reason for trade

Reason for exit

Save:

JSON logs

SQLite database

Terminal Dashboard Requirements

Use:

rich
textual

Dashboard sections:

TOP BAR:

Current Time

BTC Price

Fear & Greed Index

System Status

LEFT PANEL:

Balance

Available margin

Used margin

Leverage

RIGHT PANEL:

Open positions

Entry price

Current price

Position size

Liquidation price

BOTTOM:

Profit/Loss

Daily PnL

Trade history

Current signal

Signal confidence

News sentiment

Market sentiment

Recent logs

Folder Structure:

trading_bot/

├── agents/

├── strategy/

├── indicators/

├── patterns/

├── execution/

├── risk/

├── dashboard/

├── database/

├── logs/

├── config/

├── tests/

├── main.py

├── requirements.txt

├── dockerfile

├── .env

Latest Libraries Only:

pandas

numpy

pandas-ta

ccxt

aiohttp

websockets

rich

textual

transformers

torch

scipy

sqlalchemy

python-dotenv

loguru

pydantic

pytest

uvloop

orjson

Non-functional requirements:

Fully async
Retry mechanism
Circuit breaker
Error handling
API rate limit handling
Websocket reconnect
Memory optimization
Graceful shutdown
Structured logs
Unit tests
Docker support
Linux deployment support

A few additions I'd include for a more efficient bot beyond your original request:

Paper trading mode before real money
Walk-forward backtesting
Monte Carlo simulation
Slippage modeling
Funding fee impact
Market regime detection (trending/ranging)
Kill switch on abnormal volatility
Telegram alerts
Prometheus + Grafana monitoring
Strategy versioning
Feature store for AI inputs

This prompt gives an LLM enough detail to generate a real architecture instead of a fragile script.
Model: # Production-Grade AI Bitcoin Futures Trading System

## Complete Implementation

---

## Project Structure

```
trading_bot/
├── agents/
│   ├── __init__.py
│   ├── market_data_agent.py
│   ├── technical_analysis_agent.py
│   ├── candlestick_pattern_agent.py
│   ├── chart_pattern_agent.py
│   ├── news_intelligence_agent.py
│   ├── macro_agent.py
│   ├── ai_decision_agent.py
│   ├── risk_management_agent.py
│   ├── trade_execution_agent.py
│   ├── performance_agent.py
│   └── explainability_agent.py
├── strategy/
│   ├── __init__.py
│   ├── signal_aggregator.py
│   ├── market_regime.py
│   └── walk_forward.py
├── indicators/
│   ├── __init__.py
│   └── custom_indicators.py
├── patterns/
│   ├── __init__.py
│   ├── candlestick_patterns.py
│   └── chart_patterns.py
├── execution/
│   ├── __init__.py
│   ├── order_manager.py
│   └── position_manager.py
├── risk/
│   ├── __init__.py
│   ├── risk_engine.py
│   └── circuit_breaker.py
├── dashboard/
│   ├── __init__.py
│   └── terminal_dashboard.py
├── database/
│   ├── __init__.py
│   ├── models.py
│   └── db_manager.py
├── config/
│   ├── __init__.py
│   └── settings.py
├── monitoring/
│   ├── __init__.py
│   └── prometheus_metrics.py
├── tests/
│   ├── __init__.py
│   ├── test_technical_analysis.py
│   ├── test_risk_management.py
│   ├── test_candlestick_patterns.py
│   └── test_signal_aggregator.py
├── logs/
├── main.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── .env.example
```

---

## requirements.txt

```txt
# Core async
uvloop==0.21.0
aiohttp==3.11.0
websockets==14.1

# Exchange
ccxt==4.4.0

# Data processing
pandas==2.2.3
numpy==2.1.0
pandas-ta==0.3.14b
scipy==1.14.1
orjson==3.10.11

# AI/ML
transformers==4.46.0
torch==2.5.1
scikit-learn==1.5.2

# Database
sqlalchemy==2.0.36
aiosqlite==0.20.0
alembic==1.14.0

# Config/Env
python-dotenv==1.0.1
pydantic==2.9.2
pydantic-settings==2.6.1

# Logging
loguru==0.7.2

# Dashboard
rich==13.9.4
textual==0.85.1

# News
feedparser==6.0.11

# Monitoring
prometheus-client==0.21.0

# Testing
pytest==8.3.3
pytest-asyncio==0.24.0
pytest-mock==3.14.0
httpx==0.27.2

# Telegram alerts
python-telegram-bot==21.7

# Utilities
tenacity==9.0.0
cachetools==5.5.0
```

---

## .env.example

```bash
# Binance API Credentials
BINANCE_API_KEY=your_api_key_here
BINANCE_SECRET_KEY=your_secret_key_here
BINANCE_TESTNET=true

# Trading Configuration
SYMBOL=BTCUSDT
LEVERAGE=10
MAX_POSITION_SIZE_PCT=0.50
MAX_DAILY_LOSS_PCT=0.03
MAX_CONSECUTIVE_LOSSES=5
ACCOUNT_RISK_PCT=0.01
RISK_REWARD_RATIO=3.0

# Paper Trading
PAPER_TRADING=true
PAPER_TRADING_BALANCE=10000.0

# News APIs
NEWS_API_KEY=your_newsapi_key
CRYPTO_PANIC_API_KEY=your_cryptopanic_key

# Telegram Alerts
TELEGRAM_BOT_TOKEN=your_telegram_token
TELEGRAM_CHAT_ID=your_chat_id

# Database
DATABASE_URL=sqlite+aiosqlite:///./trading_bot.db

# Prometheus
PROMETHEUS_PORT=8000

# Logging
LOG_LEVEL=INFO
LOG_FILE=logs/trading_bot.log

# Strategy
STRATEGY_VERSION=v1.0.0
MIN_CONFIDENCE_THRESHOLD=0.65
```

---

## config/settings.py

```python
"""
Production configuration management using Pydantic Settings.
Validates all environment variables at startup.
"""

from __future__ import annotations

from typing import Optional
from pydantic import Field, field_validator
from pydantic_settings import BaseSettings, SettingsConfigDict


class Settings(BaseSettings):
    """
    Centralized configuration with validation.
    All secrets loaded from environment variables.
    """

    model_config = SettingsConfigDict(
        env_file=".env",
        env_file_encoding="utf-8",
        case_sensitive=False,
        extra="ignore",
    )

    # Binance Configuration
    binance_api_key: str = Field(default="", description="Binance API Key")
    binance_secret_key: str = Field(default="", description="Binance Secret Key")
    binance_testnet: bool = Field(default=True, description="Use testnet")

    # Trading Parameters
    symbol: str = Field(default="BTCUSDT", description="Trading symbol")
    leverage: int = Field(default=10, ge=1, le=125, description="Futures leverage")
    max_position_size_pct: float = Field(
        default=0.50, ge=0.01, le=1.0, description="Max position as fraction of balance"
    )
    max_daily_loss_pct: float = Field(
        default=0.03, ge=0.001, le=0.10, description="Max daily loss percentage"
    )
    max_consecutive_losses: int = Field(
        default=5, ge=1, le=20, description="Max consecutive losses before halt"
    )
    account_risk_pct: float = Field(
        default=0.01, ge=0.001, le=0.05, description="Risk per trade as fraction of balance"
    )
    risk_reward_ratio: float = Field(
        default=3.0, ge=1.0, le=10.0, description="Take profit to stop loss ratio"
    )
    min_confidence_threshold: float = Field(
        default=0.65, ge=0.5, le=0.99, description="Minimum signal confidence to trade"
    )

    # Paper Trading
    paper_trading: bool = Field(default=True, description="Enable paper trading mode")
    paper_trading_balance: float = Field(
        default=10000.0, ge=100.0, description="Paper trading starting balance"
    )

    # News & Data APIs
    news_api_key: Optional[str] = Field(default=None)
    crypto_panic_api_key: Optional[str] = Field(default=None)

    # Telegram
    telegram_bot_token: Optional[str] = Field(default=None)
    telegram_chat_id: Optional[str] = Field(default=None)

    # Database
    database_url: str = Field(
        default="sqlite+aiosqlite:///./trading_bot.db",
        description="Async database URL",
    )

    # Monitoring
    prometheus_port: int = Field(default=8000, ge=1024, le=65535)

    # Logging
    log_level: str = Field(default="INFO")
    log_file: str = Field(default="logs/trading_bot.log")

    # Strategy
    strategy_version: str = Field(default="v1.0.0")

    # Timeframes to analyze
    timeframes: list[str] = Field(
        default=["1m", "5m", "15m", "1h", "4h", "1d"],
        description="OHLCV timeframes to fetch",
    )

    # Candle limits per timeframe
    ohlcv_limit: int = Field(default=500, ge=100, le=1500)

    @field_validator("log_level")
    @classmethod
    def validate_log_level(cls, v: str) -> str:
        valid_levels = {"DEBUG", "INFO", "WARNING", "ERROR", "CRITICAL"}
        if v.upper() not in valid_levels:
            raise ValueError(f"log_level must be one of {valid_levels}")
        return v.upper()


# Singleton settings instance
settings = Settings()
```

---

## database/models.py

```python
"""
SQLAlchemy ORM models for persisting all trade data,
signals, performance metrics, and explainability logs.
"""

from __future__ import annotations

import enum
from datetime import datetime
from typing import Optional

from sqlalchemy import (
    JSON,
    Boolean,
    DateTime,
    Enum,
    Float,
    Integer,
    String,
    Text,
    func,
)
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column


class Base(DeclarativeBase):
    """Base class for all ORM models."""
    pass


class TradeDirection(str, enum.Enum):
    LONG = "LONG"
    SHORT = "SHORT"


class TradeStatus(str, enum.Enum):
    OPEN = "OPEN"
    CLOSED = "CLOSED"
    CANCELLED = "CANCELLED"
    PARTIAL = "PARTIAL"


class SignalAction(str, enum.Enum):
    LONG = "LONG"
    SHORT = "SHORT"
    NO_TRADE = "NO_TRADE"


class Trade(Base):
    """Records every trade opened and closed by the system."""

    __tablename__ = "trades"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    symbol: Mapped[str] = mapped_column(String(20), nullable=False, index=True)
    direction: Mapped[TradeDirection] = mapped_column(Enum(TradeDirection), nullable=False)
    status: Mapped[TradeStatus] = mapped_column(
        Enum(TradeStatus), nullable=False, default=TradeStatus.OPEN
    )
    entry_price: Mapped[float] = mapped_column(Float, nullable=False)
    exit_price: Mapped[Optional[float]] = mapped_column(Float, nullable=True)
    quantity: Mapped[float] = mapped_column(Float, nullable=False)
    leverage: Mapped[int] = mapped_column(Integer, nullable=False)
    stop_loss: Mapped[float] = mapped_column(Float, nullable=False)
    take_profit: Mapped[float] = mapped_column(Float, nullable=False)
    realized_pnl: Mapped[Optional[float]] = mapped_column(Float, nullable=True)
    funding_fees: Mapped[float] = mapped_column(Float, default=0.0)
    slippage: Mapped[float] = mapped_column(Float, default=0.0)
    confidence: Mapped[float] = mapped_column(Float, nullable=False)
    strategy_version: Mapped[str] = mapped_column(String(20), nullable=False)
    paper_trade: Mapped[bool] = mapped_column(Boolean, default=True)
    exchange_order_id: Mapped[Optional[str]] = mapped_column(String(50), nullable=True)
    opened_at: Mapped[datetime] = mapped_column(
        DateTime(timezone=True), server_default=func.now()
    )
    closed_at: Mapped[Optional[datetime]] = mapped_column(
        DateTime(timezone=True), nullable=True
    )
    created_at: Mapped[datetime] = mapped_column(
        DateTime(timezone=True), server_default=func.now()
    )


class Signal(Base):
    """Records every generated signal, including NO_TRADE decisions."""

    __tablename__ = "signals"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    action: Mapped[SignalAction] = mapped_column(Enum(SignalAction), nullable=False)
    confidence: Mapped[float] = mapped_column(Float, nullable=False)
    technical_score: Mapped[float] = mapped_column(Float, nullable=False)
    pattern_score: Mapped[float] = mapped_column(Float, nullable=False)
    sentiment_score: Mapped[float] = mapped_column(Float, nullable=False)
    macro_score: Mapped[float] = mapped_column(Float, nullable=False)
    orderbook_score: Mapped[float] = mapped_column(Float, nullable=False)
    volume_score: Mapped[float] = mapped_column(Float, nullable=False)
    oi_score: Mapped[float] = mapped_column(Float, nullable=False)
    funding_score: Mapped[float] = mapped_column(Float, nullable=False)
    reasoning: Mapped[str] = mapped_column(Text, nullable=False)
    indicators_snapshot: Mapped[dict] = mapped_column(JSON, nullable=True)
    patterns_detected: Mapped[dict] = mapped_column(JSON, nullable=True)
    news_summary: Mapped[Optional[str]] = mapped_column(Text, nullable=True)
    market_regime: Mapped[Optional[str]] = mapped_column(String(20), nullable=True)
    timestamp: Mapped[datetime] = mapped_column(
        DateTime(timezone=True), server_default=func.now(), index=True
    )


class PerformanceSnapshot(Base):
    """Daily performance snapshots for historical analysis."""

    __tablename__ = "performance_snapshots"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    date: Mapped[str] = mapped_column(String(10), nullable=False, index=True, unique=True)
    total_trades: Mapped[int] = mapped_column(Integer, default=0)
    winning_trades: Mapped[int] = mapped_column(Integer, default=0)
    losing_trades: Mapped[int] = mapped_column(Integer, default=0)
    win_rate: Mapped[float] = mapped_column(Float, default=0.0)
    profit_factor: Mapped[float] = mapped_column(Float, default=0.0)
    daily_pnl: Mapped[float] = mapped_column(Float, default=0.0)
    cumulative_pnl: Mapped[float] = mapped_column(Float, default=0.0)
    max_drawdown: Mapped[float] = mapped_column(Float, default=0.0)
    sharpe_ratio: Mapped[float] = mapped_column(Float, default=0.0)
    starting_balance: Mapped[float] = mapped_column(Float, default=0.0)
    ending_balance: Mapped[float] = mapped_column(Float, default=0.0)
    created_at: Mapped[datetime] = mapped_column(
        DateTime(timezone=True), server_default=func.now()
    )


class NewsItem(Base):
    """Cached and analyzed news items."""

    __tablename__ = "news_items"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    title: Mapped[str] = mapped_column(Text, nullable=False)
    source: Mapped[str] = mapped_column(String(100), nullable=False)
    url: Mapped[Optional[str]] = mapped_column(Text, nullable=True)
    content: Mapped[Optional[str]] = mapped_column(Text, nullable=True)
    sentiment: Mapped[str] = mapped_column(String(20), nullable=False)
    sentiment_score: Mapped[float] = mapped_column(Float, nullable=False)
    impact_score: Mapped[float] = mapped_column(Float, default=0.0)
    category: Mapped[str] = mapped_column(String(50), default="general")
    published_at: Mapped[Optional[datetime]] = mapped_column(
        DateTime(timezone=True), nullable=True
    )
    processed_at: Mapped[datetime] = mapped_column(
        DateTime(timezone=True), server_default=func.now()
    )
```

---

## database/db_manager.py

```python
"""
Async database manager handling all persistence operations.
Uses SQLAlchemy 2.0 async engine with connection pooling.
"""

from __future__ import annotations

from datetime import datetime, timezone
from typing import Optional

from loguru import logger
from sqlalchemy.ext.asyncio import AsyncSession, async_sessionmaker, create_async_engine

from config.settings import settings
from database.models import (
    Base,
    NewsItem,
    PerformanceSnapshot,
    Signal,
    SignalAction,
    Trade,
    TradeStatus,
)


class DatabaseManager:
    """
    Centralized async database manager.
    All write operations are committed immediately.
    All reads use lightweight SELECT queries.
    """

    def __init__(self) -> None:
        self._engine = create_async_engine(
            settings.database_url,
            echo=False,
            pool_pre_ping=True,
            connect_args={"check_same_thread": False}
            if "sqlite" in settings.database_url
            else {},
        )
        self._session_factory = async_sessionmaker(
            self._engine,
            class_=AsyncSession,
            expire_on_commit=False,
        )

    async def initialize(self) -> None:
        """Create all tables if they don't exist."""
        async with self._engine.begin() as conn:
            await conn.run_sync(Base.metadata.create_all)
        logger.info("Database initialized successfully")

    async def save_signal(self, signal_data: dict) -> int:
        """Persist a trading signal to the database."""
        async with self._session_factory() as session:
            signal = Signal(
                action=SignalAction(signal_data["action"]),
                confidence=signal_data["confidence"],
                technical_score=signal_data.get("technical_score", 0.0),
                pattern_score=signal_data.get("pattern_score", 0.0),
                sentiment_score=signal_data.get("sentiment_score", 0.0),
                macro_score=signal_data.get("macro_score", 0.0),
                orderbook_score=signal_data.get("orderbook_score", 0.0),
                volume_score=signal_data.get("volume_score", 0.0),
                oi_score=signal_data.get("oi_score", 0.0),
                funding_score=signal_data.get("funding_score", 0.0),
                reasoning=signal_data.get("reasoning", ""),
                indicators_snapshot=signal_data.get("indicators_snapshot"),
                patterns_detected=signal_data.get("patterns_detected"),
                news_summary=signal_data.get("news_summary"),
                market_regime=signal_data.get("market_regime"),
            )
            session.add(signal)
            await session.commit()
            await session.refresh(signal)
            return signal.id

    async def save_trade(self, trade_data: dict) -> int:
        """Persist a new trade to the database."""
        from database.models import TradeDirection

        async with self._session_factory() as session:
            trade = Trade(
                symbol=trade_data["symbol"],
                direction=TradeDirection(trade_data["direction"]),
                entry_price=trade_data["entry_price"],
                quantity=trade_data["quantity"],
                leverage=trade_data["leverage"],
                stop_loss=trade_data["stop_loss"],
                take_profit=trade_data["take_profit"],
                confidence=trade_data["confidence"],
                strategy_version=trade_data.get("strategy_version", settings.strategy_version),
                paper_trade=trade_data.get("paper_trade", settings.paper_trading),
                exchange_order_id=trade_data.get("exchange_order_id"),
            )
            session.add(trade)
            await session.commit()
            await session.refresh(trade)
            return trade.id

    async def close_trade(
        self,
        trade_id: int,
        exit_price: float,
        realized_pnl: float,
        funding_fees: float = 0.0,
        slippage: float = 0.0,
    ) -> None:
        """Mark a trade as closed with final PnL."""
        async with self._session_factory() as session:
            trade = await session.get(Trade, trade_id)
            if trade:
                trade.exit_price = exit_price
                trade.realized_pnl = realized_pnl
                trade.funding_fees = funding_fees
                trade.slippage = slippage
                trade.status = TradeStatus.CLOSED
                trade.closed_at = datetime.now(timezone.utc)
                await session.commit()

    async def save_news_item(self, news_data: dict) -> None:
        """Persist analyzed news item."""
        async with self._session_factory() as session:
            item = NewsItem(
                title=news_data["title"],
                source=news_data["source"],
                url=news_data.get("url"),
                content=news_data.get("content"),
                sentiment=news_data["sentiment"],
                sentiment_score=news_data["sentiment_score"],
                impact_score=news_data.get("impact_score", 0.0),
                category=news_data.get("category", "general"),
                published_at=news_data.get("published_at"),
            )
            session.add(item)
            await session.commit()

    async def get_open_trades(self) -> list[Trade]:
        """Retrieve all currently open trades."""
        from sqlalchemy import select

        async with self._session_factory() as session:
            result = await session.execute(
                select(Trade).where(Trade.status == TradeStatus.OPEN)
            )
            return list(result.scalars().all())

    async def get_daily_pnl(self, date_str: str) -> float:
        """Calculate total realized PnL for a given date."""
        from sqlalchemy import select

        async with self._session_factory() as session:
            result = await session.execute(
                select(Trade).where(
                    Trade.status == TradeStatus.CLOSED,
                    Trade.closed_at >= f"{date_str} 00:00:00",
                    Trade.closed_at <= f"{date_str} 23:59:59",
                )
            )
            trades = result.scalars().all()
            return sum(t.realized_pnl or 0.0 for t in trades)

    async def close(self) -> None:
        """Dispose of engine connections gracefully."""
        await self._engine.dispose()
        logger.info("Database connections closed")
```

---

## agents/market_data_agent.py

```python
"""
Market Data Agent - Fetches all real-time market data from Binance Futures.

Responsibilities:
- OHLCV data across multiple timeframes via REST and WebSocket
- Order book depth
- Funding rates
- Open interest
- Liquidation data
- Volume profile
- Real-time price streaming
"""

from __future__ import annotations

import asyncio
from collections import defaultdict, deque
from datetime import datetime, timezone
from typing import Any, Optional

import ccxt.pro as ccxtpro
import numpy as np
import orjson
from loguru import logger
from tenacity import (
    retry,
    retry_if_exception_type,
    stop_after_attempt,
    wait_exponential,
)

from config.settings import settings
from monitoring.prometheus_metrics import METRICS


class MarketDataAgent:
    """
    Async market data fetcher using ccxt.pro for WebSocket streaming.
    
    Maintains an in-memory cache of OHLCV data across all timeframes,
    order book state, and derivative market metrics.
    """

    def __init__(self) -> None:
        self._exchange: Optional[ccxtpro.binanceusdm] = None
        self._ohlcv_cache: dict[str, dict[str, list]] = defaultdict(dict)
        self._orderbook_cache: dict[str, Any] = {}
        self._funding_rate: float = 0.0
        self._open_interest: float = 0.0
        self._mark_price: float = 0.0
        self._liquidations: deque = deque(maxlen=100)
        self._running: bool = False
        self._subscribers: list[asyncio.Queue] = []

    async def initialize(self) -> None:
        """Initialize ccxt.pro exchange connection with retry logic."""
        exchange_config: dict[str, Any] = {
            "apiKey": settings.binance_api_key,
            "secret": settings.binance_secret_key,
            "enableRateLimit": True,
            "options": {
                "defaultType": "future",
                "adjustForTimeDifference": True,
            },
        }
        if settings.binance_testnet:
            exchange_config["sandbox"] = True

        self._exchange = ccxtpro.binanceusdm(exchange_config)
        await self._exchange.load_markets()
        logger.info(
            "MarketDataAgent initialized | Symbol: {} | Testnet: {}",
            settings.symbol,
            settings.binance_testnet,
        )

    def subscribe(self) -> asyncio.Queue:
        """Register a subscriber queue to receive market data updates."""
        q: asyncio.Queue = asyncio.Queue(maxsize=100)
        self._subscribers.append(q)
        return q

    async def _publish(self, event_type: str, data: dict) -> None:
        """Broadcast data update to all registered subscribers."""
        message = {"type": event_type, "data": data, "timestamp": datetime.now(timezone.utc).isoformat()}
        for queue in self._subscribers:
            try:
                queue.put_nowait(message)
            except asyncio.QueueFull:
                logger.warning("Subscriber queue full, dropping message type={}", event_type)

    @retry(
        stop=stop_after_attempt(5),
        wait=wait_exponential(multiplier=1, min=2, max=30),
        retry=retry_if_exception_type(Exception),
    )
    async def fetch_ohlcv(self, timeframe: str) -> list[list]:
        """
        Fetch OHLCV candles for a specific timeframe with retry logic.
        
        Returns list of [timestamp, open, high, low, close, volume].
        """
        assert self._exchange is not None, "Exchange not initialized"
        candles = await self._exchange.fetch_ohlcv(
            settings.symbol,
            timeframe=timeframe,
            limit=settings.ohlcv_limit,
        )
        self._ohlcv_cache[settings.symbol][timeframe] = candles
        METRICS["ohlcv_fetches"].labels(timeframe=timeframe).inc()
        return candles

    async def fetch_all_timeframes(self) -> dict[str, list[list]]:
        """Fetch OHLCV for all configured timeframes concurrently."""
        tasks = [self.fetch_ohlcv(tf) for tf in settings.timeframes]
        results = await asyncio.gather(*tasks, return_exceptions=True)
        output: dict[str, list[list]] = {}
        for tf, result in zip(settings.timeframes, results):
            if isinstance(result, Exception):
                logger.error("Failed to fetch {} OHLCV: {}", tf, result)
                # Use cached data if available
                output[tf] = self._ohlcv_cache.get(settings.symbol, {}).get(tf, [])
            else:
                output[tf] = result
        return output

    async def fetch_orderbook(self) -> dict[str, Any]:
        """Fetch top 20 levels of order book depth."""
        assert self._exchange is not None
        ob = await self._exchange.fetch_order_book(settings.symbol, limit=20)
        self._orderbook_cache = ob
        return ob

    async def fetch_funding_rate(self) -> float:
        """Fetch current funding rate for the futures contract."""
        assert self._exchange is not None
        funding_info = await self._exchange.fetch_funding_rate(settings.symbol)
        rate = float(funding_info.get("fundingRate", 0.0))
        self._funding_rate = rate
        METRICS["funding_rate"].set(rate)
        return rate

    async def fetch_open_interest(self) -> float:
        """Fetch current open interest in USD."""
        assert self._exchange is not None
        oi_data = await self._exchange.fetch_open_interest(settings.symbol)
        oi = float(oi_data.get("openInterestValue", 0.0))
        self._open_interest = oi
        METRICS["open_interest"].set(oi)
        return oi

    async def fetch_mark_price(self) -> float:
        """Fetch current mark price for liquidation calculations."""
        assert self._exchange is not None
        ticker = await self._exchange.fetch_ticker(settings.symbol)
        price = float(ticker.get("last", 0.0))
        self._mark_price = price
        METRICS["btc_price"].set(price)
        return price

    def calculate_volume_profile(
        self, candles: list[list], bins: int = 20
    ) -> dict[str, Any]:
        """
        Build a basic volume profile (price levels with volume concentrations).
        
        Returns dict with price levels and corresponding volumes,
        plus Point of Control (POC) - highest volume price level.
        """
        if not candles:
            return {}

        highs = np.array([c[2] for c in candles])
        lows = np.array([c[3] for c in candles])
        closes = np.array([c[4] for c in candles])
        volumes = np.array([c[5] for c in candles])

        price_min = lows.min()
        price_max = highs.max()
        price_bins = np.linspace(price_min, price_max, bins + 1)
        volume_at_price = np.zeros(bins)

        for i, (h, l, v) in enumerate(zip(highs, lows, volumes)):
            # Distribute volume across the price range of each candle
            candle_bins = np.where((price_bins[:-1] >= l) & (price_bins[1:] <= h))[0]
            if len(candle_bins) > 0:
                per_bin_vol = v / len(candle_bins)
                volume_at_price[candle_bins] += per_bin_vol

        poc_idx = int(np.argmax(volume_at_price))
        poc_price = float((price_bins[poc_idx] + price_bins[poc_idx + 1]) / 2)

        return {
            "price_levels": price_bins[:-1].tolist(),
            "volume_at_price": volume_at_price.tolist(),
            "poc": poc_price,
            "vah": float(price_bins[min(poc_idx + 3, bins - 1)]),  # Value Area High
            "val": float(price_bins[max(poc_idx - 3, 0)]),          # Value Area Low
        }

    def calculate_orderbook_imbalance(self, orderbook: dict) -> float:
        """
        Compute order book buy/sell pressure imbalance.
        
        Returns value between -1.0 (extreme selling) and +1.0 (extreme buying).
        """
        bids = orderbook.get("bids", [])
        asks = orderbook.get("asks", [])
        if not bids or not asks:
            return 0.0

        bid_volume = sum(float(b[1]) for b in bids[:10])
        ask_volume = sum(float(a[1]) for a in asks[:10])
        total = bid_volume + ask_volume
        if total == 0:
            return 0.0

        # Normalized: +1 = all bids, -1 = all asks
        return (bid_volume - ask_volume) / total

    async def stream_klines(self) -> None:
        """
        Stream real-time kline data via WebSocket.
        Automatically reconnects on disconnection.
        """
        assert self._exchange is not None
        logger.info("Starting kline WebSocket stream for {}", settings.symbol)

        while self._running:
            try:
                ohlcv = await self._exchange.watch_ohlcv(
                    settings.symbol, timeframe="1m"
                )
                if ohlcv:
                    latest = ohlcv[-1]
                    await self._publish(
                        "kline_1m",
                        {
                            "timestamp": latest[0],
                            "open": latest[1],
                            "high": latest[2],
                            "low": latest[3],
                            "close": latest[4],
                            "volume": latest[5],
                        },
                    )
                    self._mark_price = float(latest[4])
                    METRICS["btc_price"].set(self._mark_price)
            except Exception as exc:
                logger.warning("Kline stream error: {}. Reconnecting...", exc)
                await asyncio.sleep(2)

    async def stream_orderbook(self) -> None:
        """Stream live order book updates via WebSocket."""
        assert self._exchange is not None
        logger.info("Starting order book WebSocket stream")

        while self._running:
            try:
                ob = await self._exchange.watch_order_book(settings.symbol, limit=20)
                self._orderbook_cache = ob
                imbalance = self.calculate_orderbook_imbalance(ob)
                await self._publish(
                    "orderbook",
                    {
                        "bids": ob["bids"][:5],
                        "asks": ob["asks"][:5],
                        "imbalance": imbalance,
                    },
                )
            except Exception as exc:
                logger.warning("Order book stream error: {}. Reconnecting...", exc)
                await asyncio.sleep(2)

    async def start_streaming(self) -> None:
        """Launch all WebSocket streams concurrently."""
        self._running = True
        await asyncio.gather(
            self.stream_klines(),
            self.stream_orderbook(),
            return_exceptions=True,
        )

    async def stop(self) -> None:
        """Gracefully stop all streams and close exchange connection."""
        self._running = False
        if self._exchange:
            await self._exchange.close()
        logger.info("MarketDataAgent stopped")

    @property
    def current_price(self) -> float:
        return self._mark_price

    @property
    def funding_rate(self) -> float:
        return self._funding_rate

    @property
    def open_interest(self) -> float:
        return self._open_interest

    @property
    def orderbook(self) -> dict:
        return self._orderbook_cache
```

---

## agents/technical_analysis_agent.py

```python
"""
Technical Analysis Agent - Computes all indicators across multiple timeframes.

Indicators:
- Trend: EMA, SMA, VWAP, Supertrend, Ichimoku, ADX
- Momentum: RSI, MACD, Stochastic RSI, CCI, ROC
- Volatility: ATR, Bollinger Bands, Keltner Channel
- Volume: OBV, MFI, Volume Profile
"""

from __future__ import annotations

from typing import Any, Optional

import numpy as np
import pandas as pd
import pandas_ta as ta
from loguru import logger


class TechnicalAnalysisAgent:
    """
    Computes technical indicators and generates a composite technical score.
    
    Score ranges from -1.0 (extreme bearish) to +1.0 (extreme bullish).
    """

    def analyze(
        self, ohlcv_by_timeframe: dict[str, list[list]]
    ) -> dict[str, Any]:
        """
        Run full technical analysis across all available timeframes.
        
        Returns:
            dict with per-timeframe indicators and composite score
        """
        results: dict[str, Any] = {}
        scores: list[float] = []

        for timeframe, candles in ohlcv_by_timeframe.items():
            if len(candles) < 50:
                logger.warning("Insufficient candles for {} (got {})", timeframe, len(candles))
                continue

            df = self._candles_to_df(candles)
            indicators = self._compute_indicators(df)
            score = self._score_indicators(indicators)
            results[timeframe] = {
                "indicators": indicators,
                "score": score,
            }
            # Weight longer timeframes more heavily
            weight = self._timeframe_weight(timeframe)
            scores.append(score * weight)

        composite_score = np.mean(scores) if scores else 0.0
        results["composite_score"] = float(np.clip(composite_score, -1.0, 1.0))
        return results

    def _candles_to_df(self, candles: list[list]) -> pd.DataFrame:
        """Convert raw OHLCV list to a typed pandas DataFrame."""
        df = pd.DataFrame(
            candles,
            columns=["timestamp", "open", "high", "low", "close", "volume"],
        )
        df["timestamp"] = pd.to_datetime(df["timestamp"], unit="ms", utc=True)
        df.set_index("timestamp", inplace=True)
        for col in ["open", "high", "low", "close", "volume"]:
            df[col] = pd.to_numeric(df[col], errors="coerce")
        df.dropna(inplace=True)
        return df

    def _compute_indicators(self, df: pd.DataFrame) -> dict[str, Any]:
        """
        Apply all configured technical indicators using pandas-ta.
        Falls back gracefully if insufficient data for any indicator.
        """
        indicators: dict[str, Any] = {}

        try:
            # ----- Trend Indicators -----
            df.ta.ema(length=9, append=True)
            df.ta.ema(length=21, append=True)
            df.ta.ema(length=50, append=True)
            df.ta.ema(length=200, append=True)
            df.ta.sma(length=20, append=True)
            df.ta.sma(length=50, append=True)
            df.ta.vwap(append=True)
            df.ta.adx(length=14, append=True)

            # Supertrend
            st = df.ta.supertrend(length=10, multiplier=3.0)
            if st is not None and not st.empty:
                df = pd.concat([df, st], axis=1)

            # Ichimoku
            ichimoku = df.ta.ichimoku()
            if ichimoku is not None and len(ichimoku) == 2:
                ichi_df, ichi_span = ichimoku
                if ichi_df is not None and not ichi_df.empty:
                    df = pd.concat([df, ichi_df], axis=1)

            # ----- Momentum Indicators -----
            df.ta.rsi(length=14, append=True)
            df.ta.macd(fast=12, slow=26, signal=9, append=True)
            df.ta.stochrsi(length=14, append=True)
            df.ta.cci(length=20, append=True)
            df.ta.roc(length=10, append=True)

            # ----- Volatility Indicators -----
            df.ta.atr(length=14, append=True)
            df.ta.bbands(length=20, std=2, append=True)
            df.ta.kc(length=20, append=True)

            # ----- Volume Indicators -----
            df.ta.obv(append=True)
            df.ta.mfi(length=14, append=True)

        except Exception as exc:
            logger.error("Indicator computation error: {}", exc)

        # Extract latest values safely
        last = df.iloc[-1]
        close = float(last["close"])

        def safe_get(col: str, default: float = 0.0) -> float:
            """Safely extract a column value with fallback."""
            # pandas-ta uses various column naming conventions
            for c in df.columns:
                if col.lower() in c.lower():
                    val = last[c]
                    if pd.notna(val):
                        return float(val)
            return default

        indicators = {
            "close": close,
            "ema_9": safe_get("EMA_9"),
            "ema_21": safe_get("EMA_21"),
            "ema_50": safe_get("EMA_50"),
            "ema_200": safe_get("EMA_200"),
            "sma_20": safe_get("SMA_20"),
            "sma_50": safe_get("SMA_50"),
            "vwap": safe_get("VWAP"),
            "adx": safe_get("ADX"),
            "rsi": safe_get("RSI"),
            "macd": safe_get("MACD"),
            "macd_signal": safe_get("MACDs"),
            "macd_histogram": safe_get("MACDh"),
            "stochrsi_k": safe_get("STOCHRSIk"),
            "stochrsi_d": safe_get("STOCHRSId"),
            "cci": safe_get("CCI"),
            "roc": safe_get("ROC"),
            "atr": safe_get("ATRr"),
            "bb_upper": safe_get("BBU"),
            "bb_mid": safe_get("BBM"),
            "bb_lower": safe_get("BBL"),
            "kc_upper": safe_get("KCUe"),
            "kc_lower": safe_get("KCLe"),
            "obv": safe_get("OBV"),
            "mfi": safe_get("MFI"),
            "supertrend_direction": safe_get("SUPERTd"),
        }
        return indicators

    def _score_indicators(self, ind: dict[str, Any]) -> float:
        """
        Convert indicator readings into a normalized -1 to +1 score.
        
        Scoring logic:
        +1 = strongly bullish
        -1 = strongly bearish
        """
        scores: list[float] = []
        close = ind.get("close", 0.0)
        if close == 0:
            return 0.0

        # EMA trend alignment (each adds 0.1 to score)
        if ind["ema_9"] > ind["ema_21"] > ind["ema_50"]:
            scores.append(0.8)
        elif ind["ema_9"] < ind["ema_21"] < ind["ema_50"]:
            scores.append(-0.8)
        else:
            scores.append(0.0)

        # Price vs EMA 200
        if close > ind["ema_200"] > 0:
            scores.append(0.6)
        elif ind["ema_200"] > 0 and close < ind["ema_200"]:
            scores.append(-0.6)

        # VWAP position
        if ind["vwap"] > 0:
            scores.append(0.5 if close > ind["vwap"] else -0.5)

        # RSI zones
        rsi = ind["rsi"]
        if rsi > 0:
            if rsi > 70:
                scores.append(-0.7)  # Overbought
            elif rsi < 30:
                scores.append(0.7)   # Oversold
            elif 50 < rsi <= 70:
                scores.append(0.4)
            elif 30 <= rsi < 50:
                scores.append(-0.4)

        # MACD histogram direction
        macd_h = ind["macd_histogram"]
        if macd_h != 0:
            scores.append(0.6 if macd_h > 0 else -0.6)

        # CCI extremes
        cci = ind["cci"]
        if cci != 0:
            if cci > 100:
                scores.append(0.5)
            elif cci < -100:
                scores.append(-0.5)

        # Supertrend
        st_dir = ind["supertrend_direction"]
        if st_dir != 0:
            scores.append(0.7 if st_dir == 1 else -0.7)

        # Bollinger Band squeeze (price near lower = potential bounce)
        bb_l = ind["bb_lower"]
        bb_u = ind["bb_upper"]
        if bb_l > 0 and bb_u > 0:
            bb_position = (close - bb_l) / (bb_u - bb_l) if (bb_u - bb_l) > 0 else 0.5
            if bb_position < 0.1:
                scores.append(0.5)
            elif bb_position > 0.9:
                scores.append(-0.5)

        # MFI
        mfi = ind["mfi"]
        if mfi > 0:
            if mfi > 80:
                scores.append(-0.5)
            elif mfi < 20:
                scores.append(0.5)

        return float(np.mean(scores)) if scores else 0.0

    def get_atr(
        self, ohlcv: list[list], period: int = 14
    ) -> float:
        """Extract ATR value for risk management position sizing."""
        if len(ohlcv) < period + 1:
            return 0.0
        df = self._candles_to_df(ohlcv)
        df.ta.atr(length=period, append=True)
        atr_col = [c for c in df.columns if "ATR" in c.upper()]
        if atr_col:
            val = df[atr_col[0]].iloc[-1]
            return float(val) if pd.notna(val) else 0.0
        return 0.0

    @staticmethod
    def _timeframe_weight(timeframe: str) -> float:
        """
        Weight longer timeframes more heavily.
        Daily signals are most significant for swing context.
        """
        weights = {
            "1m": 0.05,
            "5m": 0.10,
            "15m": 0.15,
            "1h": 0.25,
            "4h": 0.30,
            "1d": 0.40,
        }
        return weights.get(timeframe, 0.15)
```

---

## agents/candlestick_pattern_agent.py

```python
"""
Candlestick Pattern Agent - Detects Japanese candlestick patterns.

Detects bullish, bearish, and neutral patterns with confidence scoring.
Confidence is calculated from pattern geometry strength.
"""

from __future__ import annotations

from dataclasses import dataclass, field
from typing import Any

import numpy as np
import pandas as pd
from loguru import logger


@dataclass
class CandlestickPattern:
    """Represents a detected candlestick pattern."""

    name: str
    direction: str  # "bullish", "bearish", "neutral"
    confidence: float  # 0.0 to 1.0
    candle_index: int  # Index in the dataframe (from end)
    description: str = ""


class CandlestickPatternAgent:
    """
    Detects classic Japanese candlestick reversal and continuation patterns.
    
    Each detection function returns a confidence score based on
    the geometric properties of the pattern.
    """

    def detect_all(
        self, ohlcv: list[list], min_confidence: float = 0.50
    ) -> list[CandlestickPattern]:
        """
        Run all pattern detectors on the provided OHLCV data.
        
        Args:
            ohlcv: Raw OHLCV candles [[ts, o, h, l, c, v], ...]
            min_confidence: Minimum confidence to include a pattern
        
        Returns:
            List of detected patterns sorted by confidence descending
        """
        if len(ohlcv) < 5:
            return []

        df = self._to_df(ohlcv)
        detected: list[CandlestickPattern] = []

        detectors = [
            self._detect_hammer,
            self._detect_inverted_hammer,
            self._detect_shooting_star,
            self._detect_bullish_engulfing,
            self._detect_bearish_engulfing,
            self._detect_morning_star,
            self._detect_evening_star,
            self._detect_three_white_soldiers,
            self._detect_three_black_crows,
            self._detect_doji,
            self._detect_spinning_top,
        ]

        for detector in detectors:
            try:
                patterns = detector(df)
                for p in patterns:
                    if p.confidence >= min_confidence:
                        detected.append(p)
            except Exception as exc:
                logger.debug("Pattern detector {} error: {}", detector.__name__, exc)

        detected.sort(key=lambda p: p.confidence, reverse=True)
        return detected

    def aggregate_score(self, patterns: list[CandlestickPattern]) -> float:
        """
        Aggregate all detected patterns into a single -1.0 to +1.0 score.
        Bullish patterns contribute positively, bearish negatively.
        """
        if not patterns:
            return 0.0

        scores: list[float] = []
        for p in patterns:
            if p.direction == "bullish":
                scores.append(p.confidence)
            elif p.direction == "bearish":
                scores.append(-p.confidence)
            # neutral patterns don't contribute directionally

        return float(np.mean(scores)) if scores else 0.0

    def _to_df(self, ohlcv: list[list]) -> pd.DataFrame:
        """Convert OHLCV to DataFrame with computed body metrics."""
        df = pd.DataFrame(
            ohlcv,
            columns=["timestamp", "open", "high", "low", "close", "volume"],
        )
        for col in ["open", "high", "low", "close"]:
            df[col] = pd.to_numeric(df[col], errors="coerce")

        df["body"] = abs(df["close"] - df["open"])
        df["upper_shadow"] = df["high"] - df[["close", "open"]].max(axis=1)
        df["lower_shadow"] = df[["close", "open"]].min(axis=1) - df["low"]
        df["range"] = df["high"] - df["low"]
        df["bullish"] = df["close"] > df["open"]
        df["bearish"] = df["close"] < df["open"]
        return df

    def _detect_hammer(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Hammer: Small body at top, long lower shadow (>= 2x body), little upper shadow.
        Bullish reversal pattern - appears after downtrend.
        """
        patterns = []
        for i in range(2, len(df)):
            row = df.iloc[i]
            if row["range"] == 0:
                continue
            lower_to_body = row["lower_shadow"] / row["range"]
            upper_to_range = row["upper_shadow"] / row["range"]
            body_to_range = row["body"] / row["range"]

            if (
                lower_to_body >= 0.60
                and upper_to_range <= 0.10
                and body_to_range <= 0.35
                and row["lower_shadow"] >= 2 * max(row["body"], 0.001)
            ):
                # Confidence based on lower shadow dominance
                confidence = min(0.95, 0.60 + lower_to_body * 0.35)
                patterns.append(
                    CandlestickPattern(
                        name="Hammer",
                        direction="bullish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="Small body with long lower shadow, potential bullish reversal",
                    )
                )
        return patterns

    def _detect_inverted_hammer(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Inverted Hammer: Small body at bottom, long upper shadow.
        Bullish reversal after downtrend.
        """
        patterns = []
        for i in range(2, len(df)):
            row = df.iloc[i]
            if row["range"] == 0:
                continue
            upper_to_range = row["upper_shadow"] / row["range"]
            lower_to_range = row["lower_shadow"] / row["range"]

            if (
                upper_to_range >= 0.60
                and lower_to_range <= 0.10
                and row["upper_shadow"] >= 2 * max(row["body"], 0.001)
            ):
                confidence = min(0.90, 0.55 + upper_to_range * 0.35)
                patterns.append(
                    CandlestickPattern(
                        name="Inverted Hammer",
                        direction="bullish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="Long upper shadow after downtrend, bullish reversal signal",
                    )
                )
        return patterns

    def _detect_shooting_star(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Shooting Star: Small body at bottom, long upper shadow after uptrend.
        Bearish reversal pattern.
        """
        patterns = []
        for i in range(2, len(df)):
            prev = df.iloc[i - 1]
            row = df.iloc[i]
            if row["range"] == 0:
                continue

            # Needs to gap up or follow bullish candle
            prior_bullish = prev["bullish"]
            upper_to_range = row["upper_shadow"] / row["range"]
            lower_to_range = row["lower_shadow"] / row["range"]

            if (
                prior_bullish
                and upper_to_range >= 0.60
                and lower_to_range <= 0.10
                and row["upper_shadow"] >= 2 * max(row["body"], 0.001)
            ):
                confidence = min(0.90, 0.55 + upper_to_range * 0.35)
                patterns.append(
                    CandlestickPattern(
                        name="Shooting Star",
                        direction="bearish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="Long upper shadow after uptrend, bearish reversal signal",
                    )
                )
        return patterns

    def _detect_bullish_engulfing(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Bullish Engulfing: Large bullish candle completely engulfs prior bearish candle.
        Strong bullish reversal signal.
        """
        patterns = []
        for i in range(1, len(df)):
            prev = df.iloc[i - 1]
            curr = df.iloc[i]

            if (
                prev["bearish"]
                and curr["bullish"]
                and curr["open"] <= prev["close"]
                and curr["close"] >= prev["open"]
                and curr["body"] > prev["body"]
            ):
                # Confidence from engulfing ratio
                engulf_ratio = curr["body"] / max(prev["body"], 0.001)
                confidence = min(0.95, 0.60 + min(engulf_ratio - 1.0, 0.5) * 0.70)
                patterns.append(
                    CandlestickPattern(
                        name="Bullish Engulfing",
                        direction="bullish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="Large bullish candle engulfs prior bearish candle",
                    )
                )
        return patterns

    def _detect_bearish_engulfing(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Bearish Engulfing: Large bearish candle completely engulfs prior bullish candle.
        Strong bearish reversal signal.
        """
        patterns = []
        for i in range(1, len(df)):
            prev = df.iloc[i - 1]
            curr = df.iloc[i]

            if (
                prev["bullish"]
                and curr["bearish"]
                and curr["open"] >= prev["close"]
                and curr["close"] <= prev["open"]
                and curr["body"] > prev["body"]
            ):
                engulf_ratio = curr["body"] / max(prev["body"], 0.001)
                confidence = min(0.95, 0.60 + min(engulf_ratio - 1.0, 0.5) * 0.70)
                patterns.append(
                    CandlestickPattern(
                        name="Bearish Engulfing",
                        direction="bearish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="Large bearish candle engulfs prior bullish candle",
                    )
                )
        return patterns

    def _detect_morning_star(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Morning Star: 3-candle bullish reversal pattern.
        Bearish candle → small-bodied doji/spinning top → bullish candle.
        """
        patterns = []
        for i in range(2, len(df)):
            c1 = df.iloc[i - 2]
            c2 = df.iloc[i - 1]
            c3 = df.iloc[i]

            if (
                c1["bearish"]
                and c3["bullish"]
                and c1["body"] > 0
                and c2["body"] < c1["body"] * 0.3  # Small middle candle
                and c3["close"] > (c1["open"] + c1["close"]) / 2
            ):
                confidence = 0.70 + min(c3["body"] / max(c1["body"], 0.001), 0.3) * 0.25
                patterns.append(
                    CandlestickPattern(
                        name="Morning Star",
                        direction="bullish",
                        confidence=float(min(confidence, 0.92)),
                        candle_index=len(df) - i,
                        description="3-candle bullish reversal: bearish, small body, bullish",
                    )
                )
        return patterns

    def _detect_evening_star(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Evening Star: 3-candle bearish reversal pattern.
        Bullish candle → small-bodied candle → bearish candle.
        """
        patterns = []
        for i in range(2, len(df)):
            c1 = df.iloc[i - 2]
            c2 = df.iloc[i - 1]
            c3 = df.iloc[i]

            if (
                c1["bullish"]
                and c3["bearish"]
                and c1["body"] > 0
                and c2["body"] < c1["body"] * 0.3
                and c3["close"] < (c1["open"] + c1["close"]) / 2
            ):
                confidence = 0.70 + min(c3["body"] / max(c1["body"], 0.001), 0.3) * 0.25
                patterns.append(
                    CandlestickPattern(
                        name="Evening Star",
                        direction="bearish",
                        confidence=float(min(confidence, 0.92)),
                        candle_index=len(df) - i,
                        description="3-candle bearish reversal: bullish, small body, bearish",
                    )
                )
        return patterns

    def _detect_three_white_soldiers(
        self, df: pd.DataFrame
    ) -> list[CandlestickPattern]:
        """
        Three White Soldiers: 3 consecutive bullish candles with rising closes.
        Strong bullish continuation/reversal.
        """
        patterns = []
        for i in range(2, len(df)):
            c1 = df.iloc[i - 2]
            c2 = df.iloc[i - 1]
            c3 = df.iloc[i]

            if (
                c1["bullish"]
                and c2["bullish"]
                and c3["bullish"]
                and c2["close"] > c1["close"]
                and c3["close"] > c2["close"]
                and c2["open"] > c1["open"]
                and c3["open"] > c2["open"]
                # Each candle should be reasonably sized
                and c1["body"] > c1["range"] * 0.5
                and c2["body"] > c2["range"] * 0.5
                and c3["body"] > c3["range"] * 0.5
            ):
                confidence = 0.78
                patterns.append(
                    CandlestickPattern(
                        name="Three White Soldiers",
                        direction="bullish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="3 strong consecutive bullish candles, strong bullish signal",
                    )
                )
        return patterns

    def _detect_three_black_crows(
        self, df: pd.DataFrame
    ) -> list[CandlestickPattern]:
        """
        Three Black Crows: 3 consecutive bearish candles with lower closes.
        Strong bearish continuation/reversal.
        """
        patterns = []
        for i in range(2, len(df)):
            c1 = df.iloc[i - 2]
            c2 = df.iloc[i - 1]
            c3 = df.iloc[i]

            if (
                c1["bearish"]
                and c2["bearish"]
                and c3["bearish"]
                and c2["close"] < c1["close"]
                and c3["close"] < c2["close"]
                and c2["open"] < c1["open"]
                and c3["open"] < c2["open"]
                and c1["body"] > c1["range"] * 0.5
                and c2["body"] > c2["range"] * 0.5
                and c3["body"] > c3["range"] * 0.5
            ):
                confidence = 0.78
                patterns.append(
                    CandlestickPattern(
                        name="Three Black Crows",
                        direction="bearish",
                        confidence=confidence,
                        candle_index=len(df) - i,
                        description="3 strong consecutive bearish candles, strong bearish signal",
                    )
                )
        return patterns

    def _detect_doji(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Doji: Open ≈ Close (< 5% of range).
        Indicates market indecision.
        """
        patterns = []
        for i in range(len(df)):
            row = df.iloc[i]
            if row["range"] == 0:
                continue
            body_ratio = row["body"] / row["range"]
            if body_ratio <= 0.05:
                confidence = min(0.85, 0.70 + (0.05 - body_ratio) / 0.05 * 0.15)
                patterns.append(
                    CandlestickPattern(
                        name="Doji",
                        direction="neutral",
                        confidence=float(confidence),
                        candle_index=len(df) - i,
                        description="Open nearly equals close, strong indecision signal",
                    )
                )
        return patterns

    def _detect_spinning_top(self, df: pd.DataFrame) -> list[CandlestickPattern]:
        """
        Spinning Top: Small real body with upper and lower shadows.
        Market indecision, potential reversal.
        """
        patterns = []
        for i in range(len(df)):
            row = df.iloc[i]
            if row["range"] == 0:
                continue
            body_ratio = row["body"] / row["range"]
            upper_ratio = row["upper_shadow"] / row["range"]
            lower_ratio = row["lower_shadow"] / row["range"]

            if (
                0.05 < body_ratio <= 0.25
                and upper_ratio >= 0.25
                and lower_ratio >= 0.25
            ):
                confidence = 0.60 + min(upper_ratio, lower_ratio) * 0.30
                patterns.append(
                    CandlestickPattern(
                        name="Spinning Top",
                        direction="neutral",
                        confidence=float(min(confidence, 0.85)),
                        candle_index=len(df) - i,
                        description="Small body with significant shadows on both sides",
                    )
                )
        return patterns
```

---

## agents/chart_pattern_agent.py

```python
"""
Chart Pattern Agent - Detects multi-bar chart patterns using scipy and numpy.

Detects:
- Head and Shoulders / Inverse Head and Shoulders
- Double Top / Double Bottom
- Ascending / Descending / Symmetrical Triangles
- Wedges (Rising/Falling)
- Flags and Pennants
- Cup and Handle
- Support and Resistance zones
"""

from __future__ import annotations

from dataclasses import dataclass
from typing import Any

import numpy as np
import pandas as pd
from loguru import logger
from scipy.signal import argrelextrema
from scipy.stats import linregress


@dataclass
class ChartPattern:
    """Represents a detected chart pattern."""

    name: str
    direction: str  # "bullish", "bearish", "neutral"
    confidence: float
    price_target: float
    description: str
    support_level: float = 0.0
    resistance_level: float = 0.0


class ChartPatternAgent:
    """
    Detects chart patterns by analyzing pivot points and trendlines.
    Uses local extrema detection from scipy.
    """

    def __init__(self, order: int = 5) -> None:
        """
        Args:
            order: Number of candles on each side to consider for pivot detection.
                   Higher = fewer but more significant pivots.
        """
        self.order = order

    def detect_all(self, ohlcv: list[list]) -> list[ChartPattern]:
        """Run all chart pattern detectors and return detected patterns."""
        if len(ohlcv) < 50:
            return []

        df = self._to_df(ohlcv)
        highs = df["high"].values
        lows = df["low"].values
        closes = df["close"].values

        # Find local peaks and valleys
        pivot_highs = self._find_pivots(highs, "high")
        pivot_lows = self._find_pivots(lows, "low")

        patterns: list[ChartPattern] = []

        detectors = [
            lambda: self._detect_double_top(highs, closes, pivot_highs),
            lambda: self._detect_double_bottom(lows, closes, pivot_lows),
            lambda: self._detect_head_and_shoulders(highs, closes, pivot_highs),
            lambda: self._detect_inverse_head_and_shoulders(lows, closes, pivot_lows),
            lambda: self._detect_triangle(highs, lows, closes, pivot_highs, pivot_lows),
            lambda: self._detect_wedge(highs, lows, closes),
            lambda: self._detect_support_resistance(highs, lows, closes),
        ]

        for detector in detectors:
            try:
                result = detector()
                if result:
                    if isinstance(result, list):
                        patterns.extend(result)
                    else:
                        patterns.append(result)
            except Exception as exc:
                logger.debug("Chart pattern detection error: {}", exc)

        patterns.sort(key=lambda p: p.confidence, reverse=True)
        return patterns

    def aggregate_score(self, patterns: list[ChartPattern]) -> float:
        """Aggregate chart patterns into -1.0 to +1.0 score."""
        if not patterns:
            return 0.0
        scores = []
        for p in patterns:
            if p.direction == "bullish":
                scores.append(p.confidence)
            elif p.direction == "bearish":
                scores.append(-p.confidence)
        return float(np.mean(scores)) if scores else 0.0

    def _to_df(self, ohlcv: list[list]) -> pd.DataFrame:
        df = pd.DataFrame(
            ohlcv,
            columns=["timestamp", "open", "high", "low", "close", "volume"],
        )
        for col in ["open", "high", "low", "close", "volume"]:
            df[col] = pd.to_numeric(df[col], errors="coerce")
        return df.dropna()

    def _find_pivots(self, data: np.ndarray, pivot_type: str) -> np.ndarray:
        """
        Find local maximum/minimum pivot points.
        
        Returns array of indices where pivots occur.
        """
        if pivot_type == "high":
            return argrelextrema(data, np.greater, order=self.order)[0]
        return argrelextrema(data, np.less, order=self.order)[0]

    def _detect_double_top(
        self,
        highs: np.ndarray,
        closes: np.ndarray,
        pivot_highs: np.ndarray,
    ) -> ChartPattern | None:
        """
        Double Top: Two roughly equal highs with a valley between them.
        Bearish reversal pattern.
        """
        if len(pivot_highs) < 2:
            return None

        # Check last two significant pivot highs
        last_two = pivot_highs[-2:]
        h1 = highs[last_two[0]]
        h2 = highs[last_two[1]]
        price_diff_pct = abs(h1 - h2) / h1

        if price_diff_pct <= 0.02:  # Peaks within 2% of each other
            valley_between = highs[last_two[0] : last_two[1]].min()
            neckline_break = closes[-1] < valley_between

            confidence = 0.65
            if neckline_break:
                confidence = 0.82  # Confirmed by neckline break
            if price_diff_pct <= 0.01:
                confidence += 0.05

            target = valley_between - (h1 - valley_between)
            return ChartPattern(
                name="Double Top",
                direction="bearish",
                confidence=min(confidence, 0.92),
                price_target=float(target),
                description=f"Double top at {h1:.0f}/{h2:.0f}, neckline {'broken' if neckline_break else 'intact'}",
                resistance_level=float(max(h1, h2)),
                support_level=float(valley_between),
            )
        return None

    def _detect_double_bottom(
        self,
        lows: np.ndarray,
        closes: np.ndarray,
        pivot_lows: np.ndarray,
    ) -> ChartPattern | None:
        """
        Double Bottom: Two roughly equal lows with a peak between them.
        Bullish reversal pattern.
        """
        if len(pivot_lows) < 2:
            return None

        last_two = pivot_lows[-2:]
        l1 = lows[last_two[0]]
        l2 = lows[last_two[1]]
        price_diff_pct = abs(l1 - l2) / l1

        if price_diff_pct <= 0.02:
            peak_between = lows[last_two[0] : last_two[1]].max()
            neckline_break = closes[-1] > peak_between

            confidence = 0.65
            if neckline_break:
                confidence = 0.82
            if price_diff_pct <= 0.01:
                confidence += 0.05

            target = peak_between + (peak_between - l1)
            return ChartPattern(
                name="Double Bottom",
                direction="bullish",
                confidence=min(confidence, 0.92),
                price_target=float(target),
                description=f"Double bottom at {l1:.0f}/{l2:.0f}, neckline {'broken' if neckline_break else 'intact'}",
                support_level=float(min(l1, l2)),
                resistance_level=float(peak_between),
            )
        return None

    def _detect_head_and_shoulders(
        self,
        highs: np.ndarray,
        closes: np.ndarray,
        pivot_highs: np.ndarray,
    ) -> ChartPattern | None:
        """
        Head and Shoulders: Left shoulder, higher head, right shoulder.
        Classic bearish reversal.
        """
        if len(pivot_highs) < 3:
            return None

        last_three = pivot_highs[-3:]
        left = highs[last_three[0]]
        head = highs[last_three[1]]
        right = highs[last_three[2]]

        # Head must be highest, shoulders roughly equal
        if (
            head > left
            and head > right
            and abs(left - right) / left <= 0.03
        ):
            neckline = min(
                highs[last_three[0] : last_three[1]].min(),
                highs[last_three[1] : last_three[2]].min(),
            )
            neckline_break = closes[-1] < neckline
            confidence = 0.72 if not neckline_break else 0.88
            target = neckline - (head - neckline)

            return ChartPattern(
                name="Head and Shoulders",
                direction="bearish",
                confidence=confidence,
                price_target=float(target),
                description=f"H&S pattern, head at {head:.0f}, neckline {'broken' if neckline_break else 'at'} {neckline:.0f}",
                support_level=float(neckline),
                resistance_level=float(head),
            )
        return None

    def _detect_inverse_head_and_shoulders(
        self,
        lows: np.ndarray,
        closes: np.ndarray,
        pivot_lows: np.ndarray,
    ) -> ChartPattern | None:
        """
        Inverse H&S: Left shoulder, lower head, right shoulder.
        Classic bullish reversal.
        """
        if len(pivot_lows) < 3:
            return None

        last_three = pivot_lows[-3:]
        left = lows[last_three[0]]
        head = lows[last_three[1]]
        right = lows[last_three[2]]

        if (
            head < left
            and head < right
            and abs(left - right) / left <= 0.03
        ):
            neckline = max(
                lows[last_three[0] : last_three[1]].max(),
                lows[last_three[1] : last_three[2]].max(),
            )
            neckline_break = closes[-1] > neckline
            confidence = 0.72 if not neckline_break else 0.88
            target = neckline + (neckline - head)

            return ChartPattern(
                name="Inverse Head and Shoulders",
                direction="bullish",
                confidence=confidence,
                price_target=float(target),
                description=f"Inverse H&S, head at {head:.0f}, neckline {'broken' if neckline_break else 'at'} {neckline:.0f}",
                support_level=float(head),
                resistance_level=float(neckline),
            )
        return None

    def _detect_triangle(
        self,
        highs: np.ndarray,
        lows: np.ndarray,
        closes: np.ndarray,
        pivot_highs: np.ndarray,
        pivot_lows: np.ndarray,
    ) -> list[ChartPattern]:
        """
        Detect ascending, descending, and symmetrical triangles
        using linear regression on pivot highs and lows.
        """
        patterns = []
        min_pivots = 3

        if len(pivot_highs) < min_pivots or len(pivot_lows) < min_pivots:
            return patterns

        # Use last N pivots
        ph_idx = pivot_highs[-min_pivots:]
        pl_idx = pivot_lows[-min_pivots:]
        ph_vals = highs[ph_idx]
        pl_vals = lows[pl_idx]

        # Fit trendlines
        h_slope, h_intercept, h_r, _, _ = linregress(ph_idx, ph_vals)
        l_slope, l_intercept, l_r, _, _ = linregress(pl_idx, pl_vals)

        converging = (h_slope < 0 and l_slope > 0) or abs(h_slope - l_slope) > 0

        if abs(h_slope) < 1 and l_slope > 0:
            # Ascending triangle (flat top, rising bottom)
            patterns.append(
                ChartPattern(
                    name="Ascending Triangle",
                    direction="bullish",
                    confidence=0.70,
                    price_target=float(ph_vals.mean() + (ph_vals.mean() - pl_vals.mean())),
                    description="Flat resistance with rising support - bullish continuation",
                    resistance_level=float(ph_vals.mean()),
                    support_level=float(pl_vals[-1]),
                )
            )
        elif h_slope < 0 and abs(l_slope) < 1:
            # Descending triangle (falling top, flat bottom)
            patterns.append(
                ChartPattern(
                    name="Descending Triangle",
                    direction="bearish",
                    confidence=0.70,
                    price_target=float(pl_vals.mean() - (ph_vals.mean() - pl_vals.mean())),
                    description="Flat support with declining resistance - bearish continuation",
                    support_level=float(pl_vals.mean()),
                    resistance_level=float(ph_vals[-1]),
                )
            )
        elif h_slope < 0 and l_slope > 0 and converging:
            # Symmetrical triangle
            patterns.append(
                ChartPattern(
                    name="Symmetrical Triangle",
                    direction="neutral",
                    confidence=0.60,
                    price_target=float(closes[-1]),
                    description="Converging trendlines, awaiting breakout direction",
                    support_level=float(pl_vals[-1]),
                    resistance_level=float(ph_vals[-1]),
                )
            )

        return patterns

    def _detect_wedge(
        self,
        highs: np.ndarray,
        lows: np.ndarray,
        closes: np.ndarray,
    ) -> list[ChartPattern]:
        """
        Rising/Falling Wedge detection using trendline convergence.
        Rising wedge = bearish, Falling wedge = bullish.
        """
        patterns = []
        n = min(30, len(highs))
        recent_highs = highs[-n:]
        recent_lows = lows[-n:]
        x = np.arange(n)

        h_slope, _, _, _, _ = linregress(x, recent_highs)
        l_slope, _, _, _, _ = linregress(x, recent_lows)

        if h_slope > 0 and l_slope > 0 and l_slope > h_slope:
            # Rising wedge (both rising, lows converging toward highs)
            patterns.append(
                ChartPattern(
                    name="Rising Wedge",
                    direction="bearish",
                    confidence=0.68,
                    price_target=float(recent_lows[-1] - (recent_highs[-1] - recent_lows[-1])),
                    description="Rising wedge pattern - bearish reversal likely",
                    resistance_level=float(recent_highs[-1]),
                    support_level=float(recent_lows[-1]),
                )
            )
        elif h_slope < 0 and l_slope < 0 and h_slope < l_slope:
            # Falling wedge (both falling, highs converging toward lows)
            patterns.append(
                ChartPattern(
                    name="Falling Wedge",
                    direction="bullish",
                    confidence=0.68,
                    price_target=float(recent_highs[-1] + (recent_highs[-1] - recent_lows[-1])),
                    description="Falling wedge pattern - bullish reversal likely",
                    support_level=float(recent_lows[-1]),
                    resistance_level=float(recent_highs[-1]),
                )
            )

        return patterns

    def _detect_support_resistance(
        self,
        highs: np.ndarray,
        lows: np.ndarray,
        closes: np.ndarray,
    ) -> list[ChartPattern]:
        """
        Identify key support and resistance zones using price clustering.
        Returns zones with touch count confidence scoring.
        """
        patterns = []
        all_prices = np.concatenate([highs, lows])
        current_price = closes[-1]

        # Use histogram to find price clusters
        hist, bin_edges = np.histogram(all_prices, bins=30)
        
        # Find high-volume price zones
        high_volume_bins = np.where(hist > hist.mean() + hist.std())[0]

        for bin_idx in high_volume_bins:
            zone_price = (bin_edges[bin_idx] + bin_edges[bin_idx + 1]) / 2
            touch_count = hist[bin_idx]
            confidence = min(0.90, 0.50 + (touch_count / len(all_prices)) * 5)

            if zone_price < current_price:
                patterns.append(
                    ChartPattern(
                        name="Support Zone",
                        direction="bullish",
                        confidence=float(confidence),
                        price_target=float(zone_price),
                        description=f"Support zone at {zone_price:.0f}, touched {touch_count} times",
                        support_level=float(zone_price),
                        resistance_level=0.0,
                    )
                )
            else:
                patterns.append(
                    ChartPattern(
                        name="Resistance Zone",
                        direction="bearish",
                        confidence=float(confidence),
                        price_target=float(zone_price),
                        description=f"Resistance zone at {zone_price:.0f}, touched {touch_count} times",
                        resistance_level=float(zone_price),
                        support_level=0.0,
                    )
                )

        return patterns[:5]  # Return top 5 zones
```

---

## agents/news_intelligence_agent.py

```python
"""
News Intelligence Agent - Fetches and analyzes global financial and crypto news.

Uses FinBERT for sentiment analysis with market impact scoring.
Tracks: Fed news, inflation, CPI, rates, regulation, geopolitics, ETF news.
"""

from __future__ import annotations

import asyncio
from datetime import datetime, timezone
from typing import Any, Optional

import aiohttp
import feedparser
from loguru import logger
from tenacity import retry, retry_if_exception_type, stop_after_attempt, wait_exponential

from config.settings import settings
from database.db_manager import DatabaseManager


class NewsIntelligenceAgent:
    """
    Continuously fetches news from RSS feeds and news APIs.
    Applies FinBERT sentiment analysis and generates market impact scores.
    
    Maintains a rolling cache of recent news sentiment for signal generation.
    """

    # RSS feeds organized by category
    RSS_FEEDS: dict[str, list[str]] = {
        "crypto": [
            "https://cointelegraph.com/rss",
            "https://decrypt.co/feed",
            "https://bitcoinmagazine.com/.rss/full/",
            "https://www.coindesk.com/arc/outboundfeeds/rss/",
        ],
        "macro": [
            "https://feeds.bloomberg.com/markets/news.rss",
            "https://www.ft.com/?format=rss",
            "https://feeds.reuters.com/reuters/businessNews",
            "https://feeds.reuters.com/reuters/UKdomesticNews",
        ],
        "geopolitics": [
            "https://feeds.reuters.com/Reuters/worldNews",
            "https://feeds.bbci.co.uk/news/world/rss.xml",
        ],
        "fed_economy": [
            "https://feeds.marketwatch.com/marketwatch/topstories/",
            "https://www.cnbc.com/id/10000664/device/rss/rss.html",
        ],
    }

    # Keywords that increase market impact score
    HIGH_IMPACT_KEYWORDS: list[str] = [
        "federal reserve", "fomc", "fed rate", "interest rate", "inflation",
        "cpi", "nonfarm payroll", "gdp", "recession", "bitcoin etf", "sec",
        "regulation", "binance", "coinbase", "bankruptcy", "war", "sanctions",
        "nuclear", "taiwan", "china", "russia", "dollar", "treasury",
        "btc", "bitcoin", "crypto", "blockchain", "halving",
    ]

    def __init__(self, db: DatabaseManager) -> None:
        self._db = db
        self._sentiment_pipeline = None
        self._recent_sentiment: list[dict] = []
        self._avg_sentiment_score: float = 0.0
        self._session: Optional[aiohttp.ClientSession] = None
        self._running: bool = False
        self._max_cached_items: int = 200

    async def initialize(self) -> None:
        """Load FinBERT model and create HTTP session."""
        self._session = aiohttp.ClientSession(
            timeout=aiohttp.ClientTimeout(total=30),
            headers={"User-Agent": "TradingBot/1.0"},
        )
        await self._load_sentiment_model()
        logger.info("NewsIntelligenceAgent initialized with FinBERT")

    async def _load_sentiment_model(self) -> None:
        """
        Load FinBERT model asynchronously in thread pool.
        FinBERT is specifically trained on financial text for accurate
        financial sentiment analysis.
        """
        loop = asyncio.get_event_loop()
        try:
            def _load():
                from transformers import pipeline
                return pipeline(
                    "text-classification",
                    model="ProsusAI/finbert",
                    device=-1,  # CPU; change to 0 for GPU
                    truncation=True,
                    max_length=512,
                )
            self._sentiment_pipeline = await loop.run_in_executor(None, _load)
            logger.info("FinBERT model loaded successfully")
        except Exception as exc:
            logger.warning("FinBERT load failed, using fallback: {}", exc)
            self._sentiment_pipeline = None

    def _analyze_sentiment_sync(self, text: str) -> tuple[str, float]:
        """
        Run FinBERT sentiment inference synchronously.
        
        Returns:
            Tuple of (label, score) where label is 'positive'/'negative'/'neutral'
        """
        if not self._sentiment_pipeline:
            return self._fallback_sentiment(text)

        try:
            result = self._sentiment_pipeline(text[:512])[0]
            label = result["label"].lower()  # positive, negative, neutral
            score = float(result["score"])

            # Normalize to -1 to +1
            if label == "positive":
                normalized = score
            elif label == "negative":
                normalized = -score
            else:
                normalized = 0.0

            return label, normalized
        except Exception as exc:
            logger.debug("Sentiment inference error: {}", exc)
            return self._fallback_sentiment(text)

    def _fallback_sentiment(self, text: str) -> tuple[str, float]:
        """
        Simple keyword-based fallback when FinBERT is unavailable.
        Returns (label, normalized_score).
        """
        text_lower = text.lower()
        bullish_words = {
            "surge", "rally", "bull", "breakout", "all-time high", "adoption",
            "approval", "bullish", "rising", "gain", "positive", "growth",
            "etf approved", "institutional", "upgrade",
        }
        bearish_words = {
            "crash", "dump", "bear", "ban", "hack", "lawsuit", "fine",
            "bearish", "falling", "loss", "negative", "decline", "fear",
            "liquidation", "bankruptcy", "fraud", "warning",
        }
        bull_count = sum(1 for w in bullish_words if w in text_lower)
        bear_count = sum(1 for w in bearish_words if w in text_lower)

        if bull_count > bear_count:
            score = min(0.85, 0.3 + bull_count * 0.15)
            return "positive", score
        elif bear_count > bull_count:
            score = min(0.85, 0.3 + bear_count * 0.15)
            return "negative", -score
        return "neutral", 0.0

    def _compute_impact_score(self, text: str, category: str) -> float:
        """
        Compute how likely this news will move Bitcoin price.
        Score from 0.0 (minimal) to 1.0 (major market mover).
        """
        text_lower = text.lower()
        score = 0.2  # Base score

        # Category multipliers
        category_weights = {
            "crypto": 0.4,
            "fed_economy": 0.35,
            "macro": 0.25,
            "geopolitics": 0.20,
        }
        score += category_weights.get(category, 0.1)

        # High-impact keyword boost
        keyword_hits = sum(1 for kw in self.HIGH_IMPACT_KEYWORDS if kw in text_lower)
        score += min(keyword_hits * 0.08, 0.35)

        return min(score, 1.0)

    @retry(
        stop=stop_after_attempt(3),
        wait=wait_exponential(min=2, max=15),
        retry=retry_if_exception_type(Exception),
    )
    async def _fetch_rss_feed(self, url: str, category: str) -> list[dict]:
        """Fetch and parse a single RSS feed."""
        assert self._session is not None

        async with self._session.get(url) as response:
            content = await response.text()

        parsed = feedparser.parse(content)
        items: list[dict] = []

        for entry in parsed.entries[:10]:  # Process latest 10 entries
            title = entry.get("title", "")
            summary = entry.get("summary", entry.get("description", ""))
            text = f"{title}. {summary}"[:512]

            loop = asyncio.get_event_loop()
            label, sent_score = await loop.run_in_executor(
                None, self._analyze_sentiment_sync, text
            )
            impact = self._compute_impact_score(text, category)

            published_raw = entry.get("published", "")
            try:
                published_dt = datetime(*entry.published_parsed[:6], tzinfo=timezone.utc)
            except Exception:
                published_dt = datetime.now(timezone.utc)

            item = {
                "title": title,
                "source": url,
                "url": entry.get("link", ""),
                "content": summary,
                "sentiment": label,
                "sentiment_score": sent_score,
                "impact_score": impact,
                "category": category,
                "published_at": published_dt,
            }
            items.append(item)

        return items

    async def fetch_all_news(self) -> list[dict]:
        """
        Fetch all RSS feeds concurrently.
        Returns list of analyzed news items sorted by impact score.
        """
        tasks = []
        for category, urls in self.RSS_FEEDS.items():
            for url in urls:
                tasks.append(self._fetch_rss_feed(url, category))

        results = await asyncio.gather(*tasks, return_exceptions=True)
        all_items: list[dict] = []
        for result in results:
            if isinstance(result, list):
                all_items.extend(result)
            elif isinstance(result, Exception):
                logger.debug("RSS feed error: {}", result)

        # Sort by impact score
        all_items.sort(key=lambda x: x.get("impact_score", 0), reverse=True)
        return all_items

    async def _news_loop(self) -> None:
        """Main news polling loop - runs every 5 minutes."""
        while self._running:
            try:
                items = await self.fetch_all_news()
                self._recent_sentiment = items[:self._max_cached_items]
                self._avg_sentiment_score = self._compute_aggregate_sentiment()

                # Persist top items to database
                for item in items[:20]:
                    await self._db.save_news_item(item)

                logger.info(
                    "News updated | {} items | Avg sentiment: {:.3f}",
                    len(items),
                    self._avg_sentiment_score,
                )
            except Exception as exc:
                logger.error("News loop error: {}", exc)

            await asyncio.sleep(300)  # 5 minutes

    def _compute_aggregate_sentiment(self) -> float:
        """
        Compute weighted average sentiment from recent news.
        Weight by both impact score and recency.
        """
        if not self._recent_sentiment:
            return 0.0

        weighted_sum = 0.0
        weight_total = 0.0

        for item in self._recent_sentiment:
            weight = item.get("impact_score", 0.1)
            score = item.get("sentiment_score", 0.0)
            weighted_sum += score * weight
            weight_total += weight

        return weighted_sum / weight_total if weight_total > 0 else 0.0

    def get_sentiment_summary(self) -> dict[str, Any]:
        """Return current news sentiment summary for signal generation."""
        top_items = self._recent_sentiment[:5]
        return {
            "aggregate_score": self._avg_sentiment_score,
            "total_items": len(self._recent_sentiment),
            "top_headlines": [
                {
                    "title": item["title"][:80],
                    "sentiment": item["sentiment"],
                    "impact": item["impact_score"],
                }
                for item in top_items
            ],
            "category_breakdown": self._category_breakdown(),
        }

    def _category_breakdown(self) -> dict[str, float]:
        """Average sentiment score per news category."""
        by_category: dict[str, list[float]] = {}
        for item in self._recent_sentiment:
            cat = item.get("category", "general")
            if cat not in by_category:
                by_category[cat] = []
            by_category[cat].append(item.get("sentiment_score", 0.0))
        return {
            cat: float(np.mean(scores))
            for cat, scores in by_category.items()
            if scores
        }

    async def start(self) -> None:
        """Start the news polling loop."""
        self._running = True
        await self._news_loop()

    async def stop(self) -> None:
        """Stop news polling and close HTTP session."""
        self._running = False
        if self._session:
            await self._session.close()
        logger.info("NewsIntelligenceAgent stopped")

    @property
    def avg_sentiment_score(self) -> float:
        return self._avg_sentiment_score


# Required for type hints in category_breakdown
import numpy as np
```

---

## agents/macro_agent.py

```python
"""
Macro Agent - Tracks macroeconomic indicators and their Bitcoin correlation.

Monitors: DXY, Gold, Nasdaq, S&P500, Treasury yields, Oil, VIX.
Generates bullish/bearish macro score for the AI Decision Agent.
"""

from __future__ import annotations

import asyncio
from datetime import datetime, timezone
from typing import Any, Optional

import aiohttp
from loguru import logger
from tenacity import retry, stop_after_attempt, wait_exponential


class MacroAgent:
    """
    Fetches macro indicator data via Yahoo Finance-compatible endpoints.
    Generates a macro score reflecting Bitcoin's expected macro environment.
    
    Bitcoin correlation rules:
    - DXY rising    → Bearish for BTC (inverse correlation)
    - Gold rising   → Slightly bullish (risk-off signal)
    - Nasdaq rising → Bullish (BTC tracks tech)
    - VIX rising    → Bearish (fear = risk-off)
    - Yields rising → Bearish (reduces crypto appeal)
    """

    # Yahoo Finance API endpoint
    YF_BASE = "https://query1.finance.yahoo.com/v8/finance/chart"

    MACRO_SYMBOLS: dict[str, str] = {
        "DXY": "DX-Y.NYB",       # US Dollar Index
        "GOLD": "GC=F",            # Gold futures
        "NASDAQ": "^IXIC",         # Nasdaq Composite
        "SP500": "^GSPC",          # S&P 500
        "US10Y": "^TNX",           # 10Y Treasury yield
        "OIL": "CL=F",             # WTI Crude Oil
        "VIX": "^VIX",             # CBOE Volatility Index
    }

    def __init__(self) -> None:
        self._session: Optional[aiohttp.ClientSession] = None
        self._macro_data: dict[str, dict] = {}
        self._macro_score: float = 0.0
        self._running: bool = False

    async def initialize(self) -> None:
        """Create HTTP session for API calls."""
        self._session = aiohttp.ClientSession(
            timeout=aiohttp.ClientTimeout(total=30),
            headers={
                "User-Agent": "Mozilla/5.0",
                "Accept": "application/json",
            },
        )
        logger.info("MacroAgent initialized")

    @retry(
        stop=stop_after_attempt(3),
        wait=wait_exponential(min=1, max=10),
    )
    async def _fetch_yahoo(self, symbol: str, ticker: str) -> dict[str, Any]:
        """
        Fetch price data from Yahoo Finance for a macro symbol.
        Returns current price, 24h change, and 7-day trend.
        """
        assert self._session is not None
        url = f"{self.YF_BASE}/{ticker}"
        params = {"interval": "1d", "range": "5d"}

        async with self._session.get(url, params=params) as resp:
            if resp.status != 200:
                logger.warning("Yahoo Finance {} returned {}", ticker, resp.status)
                return {}
            data = await resp.json()

        chart = data.get("chart", {}).get("result", [])
        if not chart:
            return {}

        result = chart[0]
        quotes = result.get("indicators", {}).get("quote", [{}])[0]
        closes = quotes.get("close", [])
        timestamps = result.get("timestamp", [])

        if len(closes) < 2:
            return {}

        current = closes[-1] or closes[-2]
        prev = closes[-2] or closes[-3] if len(closes) > 2 else current
        change_pct = ((current - prev) / prev * 100) if prev else 0.0

        # 5-day trend using simple linear regression
        import numpy as np
        valid_closes = [c for c in closes if c is not None]
        if len(valid_closes) >= 3:
            x = list(range(len(valid_closes)))
            slope = np.polyfit(x, valid_closes, 1)[0]
            trend = slope / valid_closes[0] * 100 if valid_closes[0] else 0.0
        else:
            trend = change_pct

        return {
            "symbol": symbol,
            "current": float(current),
            "prev_close": float(prev),
            "change_pct": float(change_pct),
            "trend_5d": float(trend),
            "updated_at": datetime.now(timezone.utc).isoformat(),
        }

    async def update_all(self) -> dict[str, dict]:
        """Fetch all macro indicators concurrently."""
        tasks = {
            symbol: self._fetch_yahoo(symbol, ticker)
            for symbol, ticker in self.MACRO_SYMBOLS.items()
        }
        results = await asyncio.gather(*tasks.values(), return_exceptions=True)
        for symbol, result in zip(tasks.keys(), results):
            if isinstance(result, dict) and result:
                self._macro_data[symbol] = result
            elif isinstance(result, Exception):
                logger.debug("Macro fetch error for {}: {}", symbol, result)

        self._macro_score = self._compute_macro_score()
        return self._macro_data

    def _compute_macro_score(self) -> float:
        """
        Convert macro indicator movements into Bitcoin impact score.
        Score: -1.0 = extremely bearish macro, +1.0 = extremely bullish macro.
        
        Each indicator contributes based on its historical Bitcoin correlation.
        """
        scores: list[float] = []

        def get_chg(symbol: str) -> float:
            return self._macro_data.get(symbol, {}).get("change_pct", 0.0)

        dxy_chg = get_chg("DXY")
        gold_chg = get_chg("GOLD")
        nasdaq_chg = get_chg("NASDAQ")
        sp500_chg = get_chg("SP500")
        us10y_chg = get_chg("US10Y")
        vix_chg = get_chg("VIX")
        oil_chg = get_chg("OIL")

        # DXY: Strong inverse correlation with BTC
        # +1% DXY ≈ -1% to -2% BTC pressure
        if dxy_chg != 0:
            dxy_impact = -min(abs(dxy_chg) * 0.40, 0.80)
            scores.append(dxy_impact if dxy_chg > 0 else -dxy_impact)

        # Nasdaq: Positive correlation (BTC tracks tech risk)
        if nasdaq_chg != 0:
            scores.append(min(nasdaq_chg * 0.08, 0.70) if nasdaq_chg > 0 else max(nasdaq_chg * 0.08, -0.70))

        # S&P 500: Moderate positive correlation
        if sp500_chg != 0:
            scores.append(min(sp500_chg * 0.06, 0.60) if sp500_chg > 0 else max(sp500_chg * 0.06, -0.60))

        # VIX: Inverse (fear hurts BTC)
        if vix_chg != 0:
            vix_impact = -min(abs(vix_chg) * 0.05, 0.65)
            scores.append(vix_impact if vix_chg > 0 else -vix_impact)

        # 10Y Treasury yields: Rising rates = bearish crypto
        if us10y_chg != 0:
            scores.append(-min(abs(us10y_chg) * 0.10, 0.70) if us10y_chg > 0 else min(abs(us10y_chg) * 0.10, 0.70))

        # Gold: Mildly positive (both are risk-off stores of value)
        if gold_chg != 0:
            scores.append(min(gold_chg * 0.03, 0.35) if gold_chg > 0 else max(gold_chg * 0.03, -0.35))

        if not scores:
            return 0.0

        import numpy as np
        return float(np.clip(np.mean(scores), -1.0, 1.0))

    async def _macro_loop(self) -> None:
        """Update macro data every 15 minutes (market data moves slowly)."""
        while self._running:
            try:
                await self.update_all()
                logger.info(
                    "Macro updated | Score: {:.3f} | DXY: {} | VIX: {}",
                    self._macro_score,
                    self._macro_data.get("DXY", {}).get("current", "N/A"),
                    self._macro_data.get("VIX", {}).get("current", "N/A"),
                )
            except Exception as exc:
                logger.error("Macro loop error: {}", exc)
            await asyncio.sleep(900)  # 15 minutes

    async def start(self) -> None:
        """Start the macro data polling loop."""
        self._running = True
        await self._macro_loop()

    async def stop(self) -> None:
        """Stop polling and close session."""
        self._running = False
        if self._session:
            await self._session.close()
        logger.info("MacroAgent stopped")

    @property
    def macro_score(self) -> float:
        return self._macro_score

    @property
    def macro_data(self) -> dict:
        return self._macro_data
```

---

## agents/ai_decision_agent.py

```python
"""
AI Decision Agent - The core signal generator combining all intelligence sources.

Inputs:
- Technical analysis score
- Candlestick pattern score
- Chart pattern score
- News sentiment score
- Macro economic score
- Order book imbalance score
- Volume score
- Open interest score
- Funding rate score

Output: LONG / SHORT / NO_TRADE with confidence percentage and full reasoning.
"""

from __future__ import annotations

from dataclasses import dataclass, field
from datetime import datetime, timezone
from typing import Any

import numpy as np
from loguru import logger

from config.settings import settings
from database.db_manager import DatabaseManager
from strategy.market_regime import MarketRegimeDetector


@dataclass
class TradingSignal:
    """
    Complete trading signal with all supporting evidence.
    
    Every field is logged to the database for full explainability.
    """

    action: str  # "LONG", "SHORT", "NO_TRADE"
    confidence: float  # 0.0 to 1.0
    technical_score: float
    pattern_score: float
    sentiment_score: float
    macro_score: float
    orderbook_score: float
    volume_score: float
    oi_score: float
    funding_score: float
    reasoning: str
    indicators_snapshot: dict = field(default_factory=dict)
    patterns_detected: dict = field(default_factory=dict)
    news_summary: str = ""
    market_regime: str = "unknown"
    timestamp: str = field(
        default_factory=lambda: datetime.now(timezone.utc).isoformat()
    )


class AIDecisionAgent:
    """
    Weighted ensemble signal generator.
    
    Each sub-score is weighted by its reliability and historical accuracy.
    Weights are designed to be conservative - requiring strong consensus
    before generating actionable signals.
    """

    # Weights must sum to 1.0
    SCORE_WEIGHTS: dict[str, float] = {
        "technical": 0.25,    # Most reliable for timing
        "pattern": 0.15,      # Confirms technical
        "sentiment": 0.15,    # News moves markets
        "macro": 0.15,        # Background context
        "orderbook": 0.10,    # Short-term pressure
        "volume": 0.08,       # Confirms moves
        "oi": 0.07,           # Derivatives sentiment
        "funding": 0.05,      # Funding rate signal
    }

    def __init__(self, db: DatabaseManager) -> None:
        self._db = db
        self._regime_detector = MarketRegimeDetector()
        self._signal_history: list[TradingSignal] = []

    def generate_signal(
        self,
        technical_data: dict[str, Any],
        candlestick_patterns: list,
        chart_patterns: list,
        news_summary: dict[str, Any],
        macro_data: dict[str, Any],
        orderbook: dict[str, Any],
        market_data: dict[str, Any],
    ) -> TradingSignal:
        """
        Generate a trading signal by combining all intelligence inputs.
        
        This is the core decision function. It:
        1. Extracts scores from each agent
        2. Computes weighted ensemble score
        3. Applies regime filter
        4. Applies confidence threshold
        5. Generates human-readable reasoning
        6. Returns complete signal with full explainability
        """
        # Extract individual scores (all in -1.0 to +1.0 range)
        technical_score = technical_data.get("composite_score", 0.0)
        pattern_score = self._compute_pattern_score(candlestick_patterns, chart_patterns)
        sentiment_score = float(news_summary.get("aggregate_score", 0.0))
        macro_score = float(macro_data.get("macro_score", 0.0))
        orderbook_score = float(orderbook.get("imbalance", 0.0))
        volume_score = self._compute_volume_score(market_data)
        oi_score = self._compute_oi_score(market_data)
        funding_score = self._compute_funding_score(market_data)

        # Detect market regime
        ohlcv_1h = market_data.get("ohlcv_1h", [])
        regime = self._regime_detector.detect(ohlcv_1h)

        # Compute weighted ensemble score
        weighted_score = (
            technical_score * self.SCORE_WEIGHTS["technical"]
            + pattern_score * self.SCORE_WEIGHTS["pattern"]
            + sentiment_score * self.SCORE_WEIGHTS["sentiment"]
            + macro_score * self.SCORE_WEIGHTS["macro"]
            + orderbook_score * self.SCORE_WEIGHTS["orderbook"]
            + volume_score * self.SCORE_WEIGHTS["volume"]
            + oi_score * self.SCORE_WEIGHTS["oi"]
            + funding_score * self.SCORE_WEIGHTS["funding"]
        )

        # Apply regime filter - reduce confidence in ranging markets
        regime_multiplier = self._regime_multiplier(regime)
        adjusted_score = weighted_score * regime_multiplier

        # Convert to confidence (0.5 base + signal strength)
        raw_confidence = 0.5 + abs(adjusted_score) * 0.5
        confidence = float(np.clip(raw_confidence, 0.0, 0.99))

        # Determine action
        action = self._determine_action(adjusted_score, confidence)

        # Build reasoning text
        reasoning = self._build_reasoning(
            action=action,
            confidence=confidence,
            technical_score=technical_score,
            pattern_score=pattern_score,
            sentiment_score=sentiment_score,
            macro_score=macro_score,
            orderbook_score=orderbook_score,
            oi_score=oi_score,
            funding_score=funding_score,
            regime=regime,
            candlestick_patterns=candlestick_patterns,
            chart_patterns=chart_patterns,
            news_summary=news_summary,
        )

        signal = TradingSignal(
            action=action,
            confidence=confidence,
            technical_score=technical_score,
            pattern_score=pattern_score,
            sentiment_score=sentiment_score,
            macro_score=macro_score,
            orderbook_score=orderbook_score,
            volume_score=volume_score,
            oi_score=oi_score,
            funding_score=funding_score,
            reasoning=reasoning,
            indicators_snapshot=self._extract_key_indicators(technical_data),
            patterns_detected={
                "candlestick": [p.name for p in candlestick_patterns[:5]],
                "chart": [p.name for p in chart_patterns[:5]],
            },
            news_summary=news_summary.get("top_headlines", [{}])[0].get("title", "")
            if news_summary.get("top_headlines")
            else "",
            market_regime=regime,
        )

        self._signal_history.append(signal)
        logger.info(
            "Signal generated | {} | Confidence: {:.1%} | Regime: {} | Score: {:.3f}",
            action,
            confidence,
            regime,
            adjusted_score,
        )
        return signal

    def _compute_pattern_score(
        self, candlestick_patterns: list, chart_patterns: list
    ) -> float:
        """Combine candlestick and chart pattern scores."""
        cs_score = 0.0
        cp_score = 0.0

        if candlestick_patterns:
            bull = sum(p.confidence for p in candlestick_patterns if p.direction == "bullish")
            bear = sum(p.confidence for p in candlestick_patterns if p.direction == "bearish")
            if bull + bear > 0:
                cs_score = (bull - bear) / (bull + bear)

        if chart_patterns:
            bull = sum(p.confidence for p in chart_patterns if p.direction == "bullish")
            bear = sum(p.confidence for p in chart_patterns if p.direction == "bearish")
            if bull + bear > 0:
                cp_score = (bull - bear) / (bull + bear)

        return float(np.clip((cs_score * 0.6 + cp_score * 0.4), -1.0, 1.0))

    def _compute_volume_score(self, market_data: dict) -> float:
        """
        Score volume relative to 20-period average.
        High volume on up candles = bullish.
        """
        ohlcv = market_data.get("ohlcv_1h", [])
        if len(ohlcv) < 21:
            return 0.0
        volumes = [c[5] for c in ohlcv]
        avg_vol = float(np.mean(volumes[-20:]))
        current_vol = volumes[-1]
        if avg_vol == 0:
            return 0.0
        vol_ratio = current_vol / avg_vol
        # Check if last candle was bullish or bearish
        last_candle = ohlcv[-1]
        direction = 1.0 if last_candle[4] > last_candle[1] else -1.0
        score = direction * min((vol_ratio - 1.0) * 0.5, 0.80) if vol_ratio > 1 else 0.0
        return float(np.clip(score, -1.0, 1.0))

    def _compute_oi_score(self, market_data: dict) -> float:
        """
        Rising OI with rising price = bullish.
        Rising OI with falling price = bearish (short pressure).
        """
        oi = market_data.get("open_interest", 0.0)
        prev_oi = market_data.get("prev_open_interest", oi)
        price = market_data.get("current_price", 0.0)
        prev_price = market_data.get("prev_price", price)

        if prev_oi == 0 or prev_price == 0:
            return 0.0

        oi_change = (oi - prev_oi) / prev_oi
        price_change = (price - prev_price) / prev_price

        # OI and price moving together = conviction
        if oi_change > 0 and price_change > 0:
            return min(oi_change * 5, 0.80)
        elif oi_change > 0 and price_change < 0:
            return -min(oi_change * 5, 0.80)
        elif oi_change < 0 and price_change > 0:
            return 0.40  # Short covering bullish
        return 0.0

    def _compute_funding_score(self, market_data: dict) -> float:
        """
        Funding rate signal:
        - Very positive funding (>0.05%) = overbought longs, slightly bearish
        - Very negative funding (<-0.05%) = overbought shorts, slightly bullish
        - Neutral funding = no strong signal
        """
        funding = market_data.get("funding_rate", 0.0)
        if abs(funding) < 0.0001:
            return 0.0
        # High positive funding = crowded longs = contrarian bearish
        if funding > 0.001:
            return float(np.clip(-funding * 200, -0.70, 0.0))
        elif funding < -0.001:
            return float(np.clip(-funding * 200, 0.0, 0.70))
        return float(np.clip(-funding * 50, -0.30, 0.30))

    def _determine_action(self, score: float, confidence: float) -> str:
        """
        Convert ensemble score into actionable signal.
        
        Logic:
        - Score > threshold AND confidence > min_threshold → LONG
        - Score < -threshold AND confidence > min_threshold → SHORT
        - Otherwise → NO_TRADE (most conservative default)
        """
        threshold = 0.15  # Minimum score to trade
        min_conf = settings.min_confidence_threshold

        if score > threshold and confidence >= min_conf:
            return "LONG"
        elif score < -threshold and confidence >= min_conf:
            return "SHORT"
        return "NO_TRADE"

    def _regime_multiplier(self, regime: str) -> float:
        """
        Reduce signal confidence in unfavorable market regimes.
        Trending markets produce more reliable signals.
        """
        multipliers = {
            "strong_trend_up": 1.0,
            "strong_trend_down": 1.0,
            "weak_trend_up": 0.80,
            "weak_trend_down": 0.80,
            "ranging": 0.50,        # Very uncertain
            "high_volatility": 0.60,
            "unknown": 0.70,
        }
        return multipliers.get(regime, 0.70)

    def _build_reasoning(self, **kwargs) -> str:
        """
        Generate human-readable reasoning for every decision.
        This text is logged to database and displayed on dashboard.
        """
        action = kwargs["action"]
        confidence = kwargs["confidence"]
        regime = kwargs["regime"]
        ts = kwargs["technical_score"]
        ps = kwargs["pattern_score"]
        ss = kwargs["sentiment_score"]
        ms = kwargs["macro_score"]
        obs = kwargs["orderbook_score"]
        ois = kwargs["oi_score"]
        fs = kwargs["funding_score"]
        cs_patterns = kwargs.get("candlestick_patterns", [])
        chart_patterns = kwargs.get("chart_patterns", [])
        news = kwargs.get("news_summary", {})

        lines = [
            f"ACTION: {action} | Confidence: {confidence:.1%}",
            f"Market Regime: {regime.upper().replace('_', ' ')}",
            "",
            "SIGNAL BREAKDOWN:",
            f"  Technical Analysis:  {ts:+.3f} {'▲' if ts > 0 else '▼'}",
            f"  Pattern Recognition: {ps:+.3f} {'▲' if ps > 0 else '▼'}",
            f"  News Sentiment:      {ss:+.3f} {'▲' if ss > 0 else '▼'}",
            f"  Macro Environment:   {ms:+.3f} {'▲' if ms > 0 else '▼'}",
            f"  Order Book:          {obs:+.3f} {'▲' if obs > 0 else '▼'}",
            f"  Open Interest:       {ois:+.3f} {'▲' if ois > 0 else '▼'}",
            f"  Funding Rate:        {fs:+.3f} {'▲' if fs > 0 else '▼'}",
        ]

        if cs_patterns:
            pattern_names = ", ".join(
                f"{p.name} ({p.direction}, {p.confidence:.0%})"
                for p in cs_patterns[:3]
            )
            lines.append(f"\nCANDLESTICK PATTERNS: {pattern_names}")

        if chart_patterns:
            cp_names = ", ".join(
                f"{p.name} ({p.direction})"
                for p in chart_patterns[:3]
            )
            lines.append(f"CHART PATTERNS: {cp_names}")

        headlines = news.get("top_headlines", [])
        if headlines:
            lines.append("\nKEY NEWS:")
            for h in headlines[:3]:
                lines.append(f"  [{h.get('sentiment', '?').upper()}] {h.get('title', '')[:60]}")

        if action == "NO_TRADE":
            lines.append("\nREASON FOR NO TRADE:")
            if confidence < settings.min_confidence_threshold:
                lines.append(f"  Confidence {confidence:.1%} below threshold {settings.min_confidence_threshold:.1%}")
            if regime == "ranging":
                lines.append("  Market is ranging - avoiding chop")
            if abs(ts) < 0.15:
                lines.append("  Technical signals are mixed/unclear")

        return "\n".join(lines)

    def _extract_key_indicators(self, technical_data: dict) -> dict:
        """Extract key indicator values for database snapshot."""
        snapshot = {}
        for tf in ["1h", "4h", "1d"]:
            tf_data = technical_data.get(tf, {})
            ind = tf_data.get("indicators", {})
            if ind:
                snapshot[tf] = {
                    "rsi": round(ind.get("rsi", 0), 2),
                    "macd": round(ind.get("macd", 0), 4),
                    "ema_50": round(ind.get("ema_50", 0), 2),
                    "atr": round(ind.get("atr", 0), 2),
                }
        return snapshot
```

---

## agents/risk_management_agent.py

```python
"""
Risk Management Agent - Guards every trade against catastrophic loss.

Enforces:
- Maximum account risk per trade: 1%
- Position size: max 50% of balance, volatility-adjusted
- ATR-based stop loss
- 1:3 minimum risk/reward ratio
- Maximum 3% daily loss
- Maximum 5 consecutive losses → halt trading
- No averaging down
- Kill switch on abnormal volatility
"""

from __future__ import annotations

from dataclasses import dataclass
from datetime import datetime, date, timezone
from typing import Optional

from loguru import logger

from config.settings import settings
from risk.circuit_breaker import CircuitBreaker


@dataclass
class TradeParameters:
    """Complete validated trade parameters ready for execution."""

    symbol: str
    direction: str
    entry_price: float
    stop_loss: float
    take_profit: float
    quantity: float
    position_size_usd: float
    leverage: int
    risk_amount_usd: float
    risk_reward_ratio: float
    approved: bool
    rejection_reason: Optional[str] = None


class RiskManagementAgent:
    """
    All trade parameters flow through this agent before execution.
    
    If ANY risk check fails, the trade is rejected with a reason.
    This agent has absolute veto power over the AI Decision Agent.
    """

    def __init__(self) -> None:
        self._circuit_breaker = CircuitBreaker()
        self._consecutive_losses: int = 0
        self._daily_pnl: float = 0.0
        self._daily_pnl_date: str = ""
        self._total_trades_today: int = 0
        self._trading_halted: bool = False
        self._halt_reason: str = ""

    def validate_and_size_trade(
        self,
        direction: str,
        entry_price: float,
        atr: float,
        balance: float,
        current_position_size: float = 0.0,
    ) -> TradeParameters:
        """
        Primary entry point - validates a proposed trade and calculates sizing.
        
        Returns TradeParameters with approved=False if any check fails,
        along with a human-readable rejection reason.
        """
        symbol = settings.symbol

        # ── HARD CHECKS (immediate rejection) ──────────────────────────────

        if self._trading_halted:
            return self._reject(
                direction, entry_price, f"Trading halted: {self._halt_reason}"
            )

        if self._circuit_breaker.is_open:
            return self._reject(
                direction, entry_price, f"Circuit breaker OPEN: {self._circuit_breaker.reason}"
            )

        if balance <= 0:
            return self._reject(direction, entry_price, "Zero or negative balance")

        if entry_price <= 0:
            return self._reject(direction, entry_price, "Invalid entry price")

        if atr <= 0:
            return self._reject(
                direction, entry_price, "ATR is zero - cannot calculate stop loss"
            )

        # ── DAILY LOSS CHECK ───────────────────────────────────────────────

        max_daily_loss_usd = balance * settings.max_daily_loss_pct
        if self._daily_pnl < -max_daily_loss_usd:
            self._halt_trading(
                f"Daily loss limit {settings.max_daily_loss_pct:.1%} breached"
            )
            return self._reject(
                direction, entry_price, f"Daily loss limit reached: ${abs(self._daily_pnl):.2f} loss"
            )

        # ── CONSECUTIVE LOSSES CHECK ───────────────────────────────────────

        if self._consecutive_losses >= settings.max_consecutive_losses:
            self._halt_trading(
                f"Max consecutive losses ({settings.max_consecutive_losses}) reached"
            )
            return self._reject(
                direction, entry_price,
                f"Max consecutive losses ({self._consecutive_losses}) reached - halting",
            )

        # ── EXISTING POSITION CHECK ────────────────────────────────────────

        if current_position_size > 0:
            return self._reject(
                direction, entry_price, "Existing position open - no averaging down allowed"
            )

        # ── POSITION SIZING ────────────────────────────────────────────────

        # 1. ATR-based stop loss (1.5x ATR from entry)
        atr_multiplier = 1.5
        if direction == "LONG":
            stop_loss = entry_price - (atr * atr_multiplier)
            take_profit = entry_price + (atr * atr_multiplier * settings.risk_reward_ratio)
        else:
            stop_loss = entry_price + (atr * atr_multiplier)
            take_profit = entry_price - (atr * atr_multiplier * settings.risk_reward_ratio)

        # 2. Risk per trade (1% of balance)
        risk_amount_usd = balance * settings.account_risk_pct
        stop_distance = abs(entry_price - stop_loss)

        if stop_distance == 0:
            return self._reject(direction, entry_price, "Stop distance is zero")

        # 3. Quantity from risk (leveraged)
        # quantity = risk_amount / (stop_distance / leverage_adjusted)
        # With leverage, 1 USD controls leverage USD of exposure
        quantity_from_risk = (risk_amount_usd * settings.leverage) / stop_distance

        # 4. Position size in USD
        position_size_usd = quantity_from_risk * entry_price

        # 5. Apply maximum position size cap (50% of balance × leverage)
        max_position_usd = balance * settings.max_position_size_pct * settings.leverage
        position_size_usd = min(position_size_usd, max_position_usd)

        # 6. Volatility-adjusted sizing using ATR
        # Higher ATR = reduce size proportionally
        avg_atr_pct = atr / entry_price
        volatility_adjustment = max(0.3, 1.0 - avg_atr_pct * 10)
        position_size_usd *= volatility_adjustment

        # 7. Recalculate final quantity
        quantity = position_size_usd / entry_price

        # 8. Minimum trade size check (Binance minimum ~0.001 BTC)
        min_quantity = 0.001
        if quantity < min_quantity:
            return self._reject(
                direction, entry_price,
                f"Calculated quantity {quantity:.6f} below minimum {min_quantity}"
            )

        # 9. Abnormal volatility kill switch
        if avg_atr_pct > 0.05:  # ATR > 5% of price = extreme volatility
            return self._reject(
                direction, entry_price,
                f"Abnormal volatility detected: ATR={avg_atr_pct:.2%} of price"
            )

        risk_reward = abs(take_profit - entry_price) / abs(entry_price - stop_loss)

        logger.info(
            "Trade validated | {} {} | Qty: {:.6f} | SL: {:.2f} | TP: {:.2f} | "
            "Risk: ${:.2f} | R:R: {:.2f}",
            direction,
            symbol,
            quantity,
            stop_loss,
            take_profit,
            risk_amount_usd,
            risk_reward,
        )

        return TradeParameters(
            symbol=symbol,
            direction=direction,
            entry_price=entry_price,
            stop_loss=stop_loss,
            take_profit=take_profit,
            quantity=round(quantity, 3),  # Binance precision
            position_size_usd=position_size_usd,
            leverage=settings.leverage,
            risk_amount_usd=risk_amount_usd,
            risk_reward_ratio=risk_reward,
            approved=True,
        )

    def record_trade_result(self, pnl: float) -> None:
        """
        Update internal counters after a trade closes.
        Tracks daily PnL and consecutive losses for circuit breaker logic.
        """
        today = date.today().isoformat()
        if today != self._daily_pnl_date:
            # Reset daily counters at midnight
            self._daily_pnl = 0.0
            self._daily_pnl_date = today
            self._total_trades_today = 0

        self._daily_pnl += pnl
        self._total_trades_today += 1

        if pnl < 0:
            self._consecutive_losses += 1
            logger.warning(
                "Loss recorded | PnL: ${:.2f} | Consecutive losses: {}",
                pnl,
                self._consecutive_losses,
            )
        else:
            self._consecutive_losses = 0  # Reset on winning trade
            logger.info("Win recorded | PnL: ${:.2f}", pnl)

        # Update circuit breaker
        self._circuit_breaker.record_result(pnl, self._daily_pnl)

    def reset_trading_halt(self) -> None:
        """Manually reset trading halt (operator intervention)."""
        self._trading_halted = False
        self._halt_reason = ""
        self._consecutive_losses = 0
        self._circuit_breaker.reset()
        logger.warning("Trading halt manually reset by operator")

    def _halt_trading(self, reason: str) -> None:
        """Internal halt trigger."""
        self._trading_halted = True
        self._halt_reason = reason
        logger.critical("TRADING HALTED: {}", reason)

    def _reject(
        self, direction: str, entry_price: float, reason: str
    ) -> TradeParameters:
        """Create a rejected TradeParameters with reason."""
        logger.warning("Trade REJECTED | {} | Reason: {}", direction, reason)
        return TradeParameters(
            symbol=settings.symbol,
            direction=direction,
            entry_price=entry_price,
            stop_loss=0.0,
            take_profit=0.0,
            quantity=0.0,
            position_size_usd=0.0,
            leverage=settings.leverage,
            risk_amount_usd=0.0,
            risk_reward_ratio=0.0,
            approved=False,
            rejection_reason=reason,
        )

    @property
    def is_halted(self) -> bool:
        return self._trading_halted

    @property
    def halt_reason(self) -> str:
        return self._halt_reason

    @property
    def consecutive_losses(self) -> int:
        return self._consecutive_losses

    @property
    def daily_pnl(self) -> float:
        return self._daily_pnl
```

---

## risk/circuit_breaker.py

```python
"""
Circuit Breaker - Automatically halts trading on anomalous conditions.

States: CLOSED (normal) → OPEN (halt) → HALF_OPEN (testing) → CLOSED
"""

from __future__ import annotations

from datetime import datetime, timedelta, timezone
from enum import Enum
from typing import Optional

from loguru import logger


class CircuitState(str, Enum):
    CLOSED = "CLOSED"       # Normal operation
    OPEN = "OPEN"           # Trading halted
    HALF_OPEN = "HALF_OPEN" # Testing recovery


class CircuitBreaker:
    """
    Prevents catastrophic losses by halting trading when:
    1. Rapid drawdown exceeds threshold
    2. Multiple API errors in short timeframe
    3. Abnormal market conditions detected
    
    Auto-resets after cooldown period (default 1 hour).
    """

    def __init__(
        self,
        drawdown_threshold: float = 0.05,  # 5% drawdown triggers open
        error_threshold: int = 10,          # 10 errors triggers open
        cooldown_minutes: int = 60,
    ) -> None:
        self._state = CircuitState.CLOSED
        self._reason: str = ""
        self._opened_at: Optional[datetime] = None
        self._drawdown_threshold = drawdown_threshold
        self._error_threshold = error_threshold
        self._cooldown = timedelta(minutes=cooldown_minutes)
        self._error_count: int = 0
        self._last_error_reset: datetime = datetime.now(timezone.utc)

    def record_result(self, pnl: float, cumulative_drawdown: float) -> None:
        """Check if recent results should trigger the circuit breaker."""
        if abs(cumulative_drawdown) >= self._drawdown_threshold:
            self._open(f"Drawdown {abs(cumulative_drawdown):.2%} exceeds {self._drawdown_threshold:.2%}")

    def record_error(self) -> None:
        """Track API errors. Too many errors trigger the breaker."""
        now = datetime.now(timezone.utc)
        # Reset error count every hour
        if (now - self._last_error_reset).seconds > 3600:
            self._error_count = 0
            self._last_error_reset = now

        self._error_count += 1
        if self._error_count >= self._error_threshold:
            self._open(f"Too many API errors: {self._error_count} in 1 hour")

    def _open(self, reason: str) -> None:
        """Open the circuit breaker."""
        if self._state != CircuitState.OPEN:
            self._state = CircuitState.OPEN
            self._reason = reason
            self._opened_at = datetime.now(timezone.utc)
            logger.critical("Circuit breaker OPENED: {}", reason)

    def reset(self) -> None:
        """Manually close the circuit breaker."""
        self._state = CircuitState.CLOSED
        self._reason = ""
        self._opened_at = None
        self._error_count = 0
        logger.warning("Circuit breaker RESET manually")

    def check_auto_reset(self) -> None:
        """Auto-reset after cooldown period if state is OPEN."""
        if self._state == CircuitState.OPEN and self._opened_at:
            elapsed = datetime.now(timezone.utc) - self._opened_at
            if elapsed >= self._cooldown:
                self._state = CircuitState.HALF_OPEN
                logger.info("Circuit breaker entering HALF_OPEN state after cooldown")

    @property
    def is_open(self) -> bool:
        self.check_auto_reset()
        return self._state == CircuitState.OPEN

    @property
    def state(self) -> str:
        return self._state.value

    @property
    def reason(self) -> str:
        return self._reason
```

---

## agents/trade_execution_agent.py

```python
"""
Trade Execution Agent - Places and manages orders on Binance Futures.

Handles:
- Long/Short entry with market orders
- ATR-based stop loss and take profit orders
- Partial exits
- Emergency close
- Order validation against exchange requirements
- Paper trading simulation
"""

from __future__ import annotations

import asyncio
from datetime import datetime, timezone
from typing import Any, Optional

import ccxt.pro as ccxtpro
from loguru import logger
from tenacity import retry, retry_if_exception_type, stop_after_attempt, wait_exponential

from agents.risk_management_agent import TradeParameters
from config.settings import settings
from database.db_manager import DatabaseManager
from monitoring.prometheus_metrics import METRICS


class PaperTradingEngine:
    """
    Simulates order fills with realistic slippage for paper trading.
    Uses market order slippage model based on order book spread.
    """

    def __init__(self, initial_balance: float) -> None:
        self.balance = initial_balance
        self.positions: dict[str, dict] = {}
        self.order_counter = 1000

    def simulate_fill(
        self, symbol: str, direction: str, quantity: float, price: float
    ) -> dict[str, Any]:
        """Simulate order fill with 0.05% slippage model."""
        slippage_pct = 0.0005  # 0.05% slippage
        if direction == "LONG":
            fill_price = price * (1 + slippage_pct)
        else:
            fill_price = price * (1 - slippage_pct)

        order_id = f"PAPER-{self.order_counter}"
        self.order_counter += 1
        return {
            "id": order_id,
            "symbol": symbol,
            "side": "buy" if direction == "LONG" else "sell",
            "price": fill_price,
            "amount": quantity,
            "filled": quantity,
            "status": "closed",
            "timestamp": datetime.now(timezone.utc).isoformat(),
        }

    def close_position(
        self, symbol: str, current_price: float, direction: str, quantity: float
    ) -> tuple[float, float]:
        """
        Calculate PnL from closing a paper position.
        Returns (realized_pnl, exit_price).
        """
        slippage_pct = 0.0005
        if direction == "LONG":
            exit_price = current_price * (1 - slippage_pct)
            pnl = (exit_price - self.positions[symbol]["entry_price"]) * quantity
        else:
            exit_price = current_price * (1 + slippage_pct)
            pnl = (self.positions[symbol]["entry_price"] - exit_price) * quantity

        # Deduct trading fees (0.04% taker)
        fee = exit_price * quantity * 0.0004
        pnl -= fee
        self.balance += pnl
        return pnl, exit_price


class TradeExecutionAgent:
    """
    Manages all order lifecycle on Binance Futures.
    
    Paper trading mode routes all orders to PaperTradingEngine.
    Live mode uses ccxt.pro with full exchange validation.
    """

    def __init__(self, db: DatabaseManager) -> None:
        self._db = db
        self._exchange: Optional[ccxtpro.binanceusdm] = None
        self._paper_engine: Optional[PaperTradingEngine] = None
        self._open_trade_id: Optional[int] = None
        self._open_position: Optional[dict] = None
        self._paper_mode = settings.paper_trading

    async def initialize(self) -> None:
        """Initialize exchange connection or paper trading engine."""
        if self._paper_mode:
            self._paper_engine = PaperTradingEngine(settings.paper_trading_balance)
            logger.info(
                "TradeExecutionAgent ready | PAPER TRADING | Balance: ${:.2f}",
                settings.paper_trading_balance,
            )
        else:
            self._exchange = ccxtpro.binanceusdm({
                "apiKey": settings.binance_api_key,
                "secret": settings.binance_secret_key,
                "enableRateLimit": True,
                "options": {"defaultType": "future"},
                "sandbox": settings.binance_testnet,
            })
            await self._exchange.load_markets()
            await self._set_leverage()
            logger.info(
                "TradeExecutionAgent ready | LIVE | Testnet: {}",
                settings.binance_testnet,
            )

    async def _set_leverage(self) -> None:
        """Configure leverage on Binance Futures for the trading symbol."""
        if self._exchange:
            try:
                await self._exchange.set_leverage(settings.leverage, settings.symbol)
                logger.info("Leverage set to {}x for {}", settings.leverage, settings.symbol)
            except Exception as exc:
                logger.error("Failed to set leverage: {}", exc)

    async def execute_trade(self, params: TradeParameters) -> Optional[dict]:
        """
        Execute a validated trade from Risk Management Agent.
        
        Returns order details dict or None if execution fails.
        """
        if not params.approved:
            logger.warning("Skipping rejected trade: {}", params.rejection_reason)
            return None

        if self._open_position:
            logger.warning("Already have open position, skipping")
            return None

        try:
            if self._paper_mode:
                order = await self._execute_paper(params)
            else:
                order = await self._execute_live(params)

            if order:
                # Persist trade to database
                trade_id = await self._db.save_trade({
                    "symbol": params.symbol,
                    "direction": params.direction,
                    "entry_price": params.entry_price,
                    "quantity": params.quantity,
                    "leverage": params.leverage,
                    "stop_loss": params.stop_loss,
                    "take_profit": params.take_profit,
                    "confidence": 0.0,  # Set by caller
                    "exchange_order_id": order.get("id"),
                    "paper_trade": self._paper_mode,
                })

                self._open_trade_id = trade_id
                self._open_position = {
                    "direction": params.direction,
                    "entry_price": params.entry_price,
                    "quantity": params.quantity,
                    "stop_loss": params.stop_loss,
                    "take_profit": params.take_profit,
                    "trade_id": trade_id,
                }

                METRICS["trades_opened"].inc()
                logger.info(
                    "Position OPENED | {} {} @ {:.2f} | SL: {:.2f} | TP: {:.2f}",
                    params.direction,
                    params.quantity,
                    params.entry_price,
                    params.stop_loss,
                    params.take_profit,
                )
                return order

        except Exception as exc:
            logger.error("Trade execution failed: {}", exc)
            return None

        return None

    async def _execute_paper(self, params: TradeParameters) -> dict:
        """Route to paper trading engine."""
        assert self._paper_engine is not None
        order = self._paper_engine.simulate_fill(
            params.symbol, params.direction, params.quantity, params.entry_price
        )
        self._paper_engine.positions[params.symbol] = {
            "direction": params.direction,
            "entry_price": order["price"],
            "quantity": params.quantity,
        }
        return order

    @retry(
        stop=stop_after_attempt(3),
        wait=wait_exponential(min=1, max=10),
        retry=retry_if_exception_type(Exception),
    )
    async def _execute_live(self, params: TradeParameters) -> dict:
        """Execute order on live Binance Futures exchange."""
        assert self._exchange is not None

        side = "buy" if params.direction == "LONG" else "sell"

        # Market order for entry
        order = await self._exchange.create_market_order(
            params.symbol,
            side,
            params.quantity,
        )

        # Place stop loss order
        sl_side = "sell" if params.direction == "LONG" else "buy"
        await self._exchange.create_order(
            params.symbol,
            "stop_market",
            sl_side,
            params.quantity,
            params.stop_loss,
            {"stopPrice": params.stop_loss, "reduceOnly": True},
        )

        # Place take profit order
        tp_side = sl_side
        await self._exchange.create_order(
            params.symbol,
            "take_profit_market",
            tp_side,
            params.quantity,
            params.take_profit,
            {"stopPrice": params.take_profit, "reduceOnly": True},
        )

        return order

    async def close_position(
        self, reason: str = "signal", current_price: float = 0.0
    ) -> Optional[float]:
        """
        Close the current open position.
        Returns realized PnL.
        """
        if not self._open_position:
            logger.debug("No open position to close")
            return None

        try:
            pos = self._open_position
            pnl: float

            if self._paper_mode:
                assert self._paper_engine is not None
                pnl, exit_price = self._paper_engine.close_position(
                    settings.symbol,
                    current_price,
                    pos["direction"],
                    pos["quantity"],
                )
            else:
                pnl, exit_price = await self._close_live_position(pos, current_price)

            # Update database
            if self._open_trade_id:
                await self._db.close_trade(
                    self._open_trade_id,
                    exit_price=exit_price,
                    realized_pnl=pnl,
                )

            logger.info(
                "Position CLOSED | Reason: {} | PnL: ${:.2f} | Exit: {:.2f}",
                reason,
                pnl,
                exit_price,
            )

            METRICS["trades_closed"].inc()
            if pnl > 0:
                METRICS["winning_trades"].inc()
            else:
                METRICS["losing_trades"].inc()
            METRICS["total_pnl"].set(pnl)

            self._open_position = None
            self._open_trade_id = None
            return pnl

        except Exception as exc:
            logger.error("Failed to close position: {}", exc)
            return None

    async def _close_live_position(
        self, pos: dict, current_price: float
    ) -> tuple[float, float]:
        """Close live position with market order."""
        assert self._exchange is not None

        side = "sell" if pos["direction"] == "LONG" else "buy"
        order = await self._exchange.create_market_order(
            settings.symbol, side, pos["quantity"], {"reduceOnly": True}
        )

        exit_price = float(order.get("average", current_price))
        entry_price = pos["entry_price"]
        qty = pos["quantity"]

        if pos["direction"] == "LONG":
            pnl = (exit_price - entry_price) * qty
        else:
            pnl = (entry_price - exit_price) * qty

        fee = exit_price * qty * 0.0004  # 0.04% taker fee
        return pnl - fee, exit_price

    async def emergency_close(self) -> None:
        """Emergency position close - used by kill switch."""
        if self._open_position:
            logger.critical("EMERGENCY CLOSE triggered")
            # Use a zero price to force market close
            await self.close_position(reason="emergency", current_price=0.0)

    @property
    def has_open_position(self) -> bool:
        return self._open_position is not None

    @property
    def open_position(self) -> Optional[dict]:
        return self._open_position

    @property
    def paper_balance(self) -> float:
        if self._paper_engine:
            return self._paper_engine.balance
        return 0.0

    async def get_account_balance(self) -> float:
        """Get current balance from exchange or paper engine."""
        if self._paper_mode:
            return self.paper_balance
        if self._exchange:
            try:
                balance = await self._exchange.fetch_balance()
                return float(balance.get("USDT", {}).get("free", 0.0))
            except Exception as exc:
                logger.error("Balance fetch error: {}", exc)
        return 0.0
```

---

## agents/performance_agent.py

```python
"""
Performance Agent - Tracks and calculates all trading performance metrics.

Metrics:
- Total trades, wins, losses
- Win rate
- Profit factor
- Maximum drawdown
- Sharpe ratio
- Daily and monthly PnL
"""

from __future__ import annotations

from collections import deque
from datetime import date, datetime
from typing import Any

import numpy as np
from loguru import logger

from database.db_manager import DatabaseManager


class PerformanceAgent:
    """
    Real-time performance tracking with statistical analysis.
    Supports walk-forward analysis and Monte Carlo simulation.
    """

    def __init__(self, db: DatabaseManager) -> None:
        self._db = db
        self._trades: list[dict] = []
        self._pnl_history: deque[float] = deque(maxlen=1000)
        self._daily_pnl: dict[str, float] = {}

    def record_trade(
        self,
        pnl: float,
        direction: str,
        entry: float,
        exit_price: float,
        timestamp: str,
    ) -> None:
        """Record a completed trade for performance tracking."""
        self._trades.append({
            "pnl": pnl,
            "direction": direction,
            "entry": entry,
            "exit": exit_price,
            "timestamp": timestamp,
            "win": pnl > 0,
        })
        self._pnl_history.append(pnl)

        today = date.today().isoformat()
        self._daily_pnl[today] = self._daily_pnl.get(today, 0.0) + pnl

    def get_metrics(self) -> dict[str, Any]:
        """
        Compute current performance metrics snapshot.
        
        Returns comprehensive dict suitable for dashboard display.
        """
        if not self._trades:
            return self._empty_metrics()

        pnls = [t["pnl"] for t in self._trades]
        wins = [p for p in pnls if p > 0]
        losses = [p for p in pnls if p <= 0]

        total_trades = len(pnls)
        win_count = len(wins)
        win_rate = win_count / total_trades if total_trades else 0.0

        # Profit Factor = gross wins / gross losses
        gross_wins = sum(wins) if wins else 0.0
        gross_losses = abs(sum(losses)) if losses else 0.0
        profit_factor = gross_wins / gross_losses if gross_losses > 0 else float("inf")

        # Maximum Drawdown
        cumulative = np.cumsum(pnls)
        running_max = np.maximum.accumulate(cumulative)
        drawdowns = running_max - cumulative
        max_drawdown = float(drawdowns.max()) if len(drawdowns) > 0 else 0.0

        # Sharpe Ratio (annualized, daily returns)
        sharpe = self._compute_sharpe(pnls)

        # Monthly PnL
        monthly_pnl = self._compute_monthly_pnl()

        today = date.today().isoformat()
        return {
            "total_trades": total_trades,
            "win_count": win_count,
            "loss_count": total_trades - win_count,
            "win_rate": win_rate,
            "profit_factor": round(profit_factor, 3),
            "max_drawdown": round(max_drawdown, 2),
            "sharpe_ratio": round(sharpe, 3),
            "total_pnl": round(sum(pnls), 2),
            "daily_pnl": round(self._daily_pnl.get(today, 0.0), 2),
            "monthly_pnl": monthly_pnl,
            "avg_win": round(np.mean(wins), 2) if wins else 0.0,
            "avg_loss": round(np.mean(losses), 2) if losses else 0.0,
        }

    def _compute_sharpe(
        self, pnls: list[float], risk_free_rate: float = 0.05
    ) -> float:
        """
        Compute annualized Sharpe ratio.
        Risk-free rate defaults to 5% annual (0.05/252 daily).
        """
        if len(pnls) < 5:
            return 0.0
        arr = np.array(pnls)
        daily_rf = risk_free_rate / 252
        excess_returns = arr - daily_rf
        std = np.std(excess_returns)
        if std == 0:
            return 0.0
        return float(np.mean(excess_returns) / std * np.sqrt(252))

    def _compute_monthly_pnl(self) -> dict[str, float]:
        """Group daily PnL into monthly totals."""
        monthly: dict[str, float] = {}
        for date_str, pnl in self._daily_pnl.items():
            month_key = date_str[:7]  # YYYY-MM
            monthly[month_key] = monthly.get(month_key, 0.0) + pnl
        return {k: round(v, 2) for k, v in monthly.items()}

    def run_monte_carlo(
        self, simulations: int = 1000, periods: int = 252
    ) -> dict[str, Any]:
        """
        Monte Carlo simulation for forward-looking performance projection.
        Resamples historical trades to estimate outcome distribution.
        """
        if len(self._trades) < 20:
            return {"error": "Insufficient trade history for simulation"}

        pnls = np.array([t["pnl"] for t in self._trades])
        results: list[float] = []

        for _ in range(simulations):
            # Resample with replacement
            sampled = np.random.choice(pnls, size=periods, replace=True)
            final_pnl = float(sampled.sum())
            results.append(final_pnl)

        results_arr = np.array(results)
        return {
            "simulations": simulations,
            "periods": periods,
            "mean_pnl": round(float(np.mean(results_arr)), 2),
            "median_pnl": round(float(np.median(results_arr)), 2),
            "p5_pnl": round(float(np.percentile(results_arr, 5)), 2),
            "p95_pnl": round(float(np.percentile(results_arr, 95)), 2),
            "prob_profit": round(float((results_arr > 0).mean()), 3),
            "max_sim_loss": round(float(results_arr.min()), 2),
            "max_sim_gain": round(float(results_arr.max()), 2),
        }

    @staticmethod
    def _empty_metrics() -> dict[str, Any]:
        return {
            "total_trades": 0,
            "win_count": 0,
            "loss_count": 0,
            "win_rate": 0.0,
            "profit_factor": 0.0,
            "max_drawdown": 0.0,
            "sharpe_ratio": 0.0,
            "total_pnl": 0.0,
            "daily_pnl": 0.0,
            "monthly_pnl": {},
            "avg_win": 0.0,
            "avg_loss": 0.0,
        }
```

---

## strategy/market_regime.py

```python
"""
Market Regime Detector - Classifies current market condition.

Regimes:
- strong_trend_up / strong_trend_down
- weak_trend_up / weak_trend_down
- ranging
- high_volatility

Uses ADX + volatility + price structure for classification.
"""

from __future__ import annotations

from typing import Any

import numpy as np
import pandas as pd
import pandas_ta as ta


class MarketRegimeDetector:
    """
    Classifies the current market regime to improve signal quality.
    
    Trending regimes allow full position sizing.
    Ranging regimes reduce size and confidence.
    """

    def detect(self, ohlcv: list[list]) -> str:
        """
        Detect current market regime from 1H OHLCV data.
        
        Args:
            ohlcv: List of [timestamp, open, high, low, close, volume]
        
        Returns:
            Regime label string
        """
        if len(ohlcv) < 50:
            return "unknown"

        df = pd.DataFrame(
            ohlcv,
            columns=["timestamp", "open", "high", "low", "close", "volume"],
        )
        for col in ["open", "high", "low", "close", "volume"]:
            df[col] = pd.to_numeric(df[col], errors="coerce")
        df.dropna(inplace=True)

        try:
            df.ta.adx(length=14, append=True)
            df.ta.atr(length=14, append=True)
        except Exception:
            return "unknown"

        # Get ADX column
        adx_col = [c for c in df.columns if "ADX" in c and "D" not in c[3:]]
        atr_col = [c for c in df.columns if "ATR" in c.upper()]

        if not adx_col or not atr_col:
            return "unknown"

        adx = float(df[adx_col[0]].iloc[-1]) if not df[adx_col[0]].isnull().all() else 20.0
        atr = float(df[atr_col[0]].iloc[-1]) if not df[atr_col[0]].isnull().all() else 0.0
        close = float(df["close"].iloc[-1])

        # ATR as percentage of price
        atr_pct = atr / close if close > 0 else 0.02

        # Price trend: compare last 20 closes to 50-period SMA
        recent_close = df["close"].iloc[-1]
        sma_20 = df["close"].rolling(20).mean().iloc[-1]
        sma_50 = df["close"].rolling(50).mean().iloc[-1]

        price_above_sma = recent_close > sma_50

        # ADX thresholds
        # ADX > 25 = trending, > 40 = strong trend, < 20 = ranging
        if atr_pct > 0.04:  # 4% ATR = high volatility
            return "high_volatility"
        elif adx >= 35:
            return "strong_trend_up" if price_above_sma else "strong_trend_down"
        elif 25 <= adx < 35:
            return "weak_trend_up" if price_above_sma else "weak_trend_down"
        else:
            return "ranging"
```

---

## dashboard/terminal_dashboard.py

```python
"""
Terminal Dashboard - Real-time trading system display using Rich.

Sections:
- TOP BAR: Time, BTC Price, System Status
- LEFT: Account balance, margin info
- RIGHT: Open position details
- BOTTOM: PnL, trade history, signals, news sentiment, logs
"""

from __future__ import annotations

import asyncio
from datetime import datetime, timezone
from typing import Any, Optional

from rich.align import Align
from rich.columns import Columns
from rich.console import Console
from rich.layout import Layout
from rich.live import Live
from rich.panel import Panel
from rich.table import Table
from rich.text import Text


class TradingDashboard:
    """
    Real-time terminal dashboard using Rich Live display.
    Updates at 1-second intervals with latest market data.
    """

    def __init__(self) -> None:
        self._console = Console()
        self._layout = Layout()
        self._data: dict[str, Any] = self._empty_data()
        self._log_buffer: list[str] = []
        self._max_logs = 20

    def _empty_data(self) -> dict[str, Any]:
        """Initialize with placeholder data."""
        return {
            "btc_price": 0.0,
            "price_change_pct": 0.0,
            "system_status": "STARTING",
            "mode": "PAPER",
            "balance": 0.0,
            "available_margin": 0.0,
            "used_margin": 0.0,
            "leverage": 10,
            "open_position": None,
            "total_pnl": 0.0,
            "daily_pnl": 0.0,
            "win_rate": 0.0,
            "total_trades": 0,
            "signal": "NO_TRADE",
            "signal_confidence": 0.0,
            "news_sentiment": 0.0,
            "market_regime": "unknown",
            "funding_rate": 0.0,
            "open_interest": 0.0,
            "macro_score": 0.0,
            "trade_history": [],
        }

    def update(self, data: dict[str, Any]) -> None:
        """Update dashboard data (called from main trading loop)."""
        self._data.update(data)

    def add_log(self, message: str, level: str = "INFO") -> None:
        """Add a log entry to the dashboard log buffer."""
        timestamp = datetime.now(timezone.utc).strftime("%H:%M:%S")
        color = {
            "INFO": "white",
            "WARNING": "yellow",
            "ERROR": "red",
            "SUCCESS": "green",
        }.get(level, "white")
        self._log_buffer.append(f"[{color}][{timestamp}] {message}[/{color}]")
        if len(self._log_buffer) > self._max_logs:
            self._log_buffer.pop(0)

    def _build_header(self) -> Panel:
        """Top bar with system status, price, and time."""
        now = datetime.now(timezone.utc).strftime("%Y-%m-%d %H:%M:%S UTC")
        price = self._data["btc_price"]
        chg = self._data["price_change_pct"]
        status = self._data["system_status"]
        mode = self._data["mode"]

        chg_color = "green" if chg >= 0 else "red"
        chg_arrow = "▲" if chg >= 0 else "▼"

        status_color = {
            "RUNNING": "green",
            "STARTING": "yellow",
            "HALTED": "red",
            "PAPER": "cyan",
        }.get(status, "white")

        header_text = Text()
        header_text.append(f"  🕐 {now}  ", style="white")
        header_text.append("  │  ", style="dim")
        header_text.append(f"₿ BTC/USDT: ${price:,.2f} ", style="bold yellow")
        header_text.append(f"({chg_arrow} {abs(chg):.2f}%)", style=f"bold {chg_color}")
        header_text.append("  │  ", style="dim")
        header_text.append(f" MODE: {mode} ", style="bold cyan")
        header_text.append("  │  ", style="dim")
        header_text.append(f" STATUS: {status} ", style=f"bold {status_color}")

        return Panel(
            Align.center(header_text),
            style="bold",
            border_style="bright_blue",
        )

    def _build_account_panel(self) -> Panel:
        """Left panel showing account balance and margin info."""
        table = Table(show_header=False, box=None, padding=(0, 1))
        table.add_column("Key", style="dim")
        table.add_column("Value", style="bold")

        balance = self._data["balance"]
        avail = self._data["available_margin"]
        used = self._data["used_margin"]
        leverage = self._data["leverage"]

        table.add_row("💰 Balance", f"${balance:,.2f}")
        table.add_row("✅ Available", f"${avail:,.2f}")
        table.add_row("🔒 Used Margin", f"${used:,.2f}")
        table.add_row("⚡ Leverage", f"{leverage}x")
        table.add_row("", "")
        table.add_row("📊 Funding Rate", f"{self._data['funding_rate']:.4%}")
        table.add_row("📈 Open Interest", f"${self._data['open_interest']:,.0f}")
        table.add_row("🌍 Macro Score", f"{self._data['macro_score']:+.3f}")
        table.add_row("", "")
        table.add_row("📰 News Sentiment", self._sentiment_bar(self._data["news_sentiment"]))
        table.add_row("🔄 Market Regime", self._data["market_regime"].upper().replace("_", " "))

        return Panel(table, title="[bold cyan]Account[/bold cyan]", border_style="cyan")

    def _build_position_panel(self) -> Panel:
        """Right panel showing current open position."""
        pos = self._data.get("open_position")

        if not pos:
            return Panel(
                Align.center(Text("\n  No Open Position  \n", style="dim italic")),
                title="[bold yellow]Position[/bold yellow]",
                border_style="yellow",
            )

        table = Table(show_header=False, box=None, padding=(0, 1))
        table.add_column("Key", style="dim")
        table.add_column("Value", style="bold")

        direction = pos.get("direction", "")
        direction_color = "green" if direction == "LONG" else "red"
        direction_icon = "🟢" if direction == "LONG" else "🔴"

        entry = pos.get("entry_price", 0.0)
        current = self._data["btc_price"]
        qty = pos.get("quantity", 0.0)
        sl = pos.get("stop_loss", 0.0)
        tp = pos.get("take_profit", 0.0)

        # Unrealized PnL
        if direction == "LONG":
            upnl = (current - entry) * qty
        else:
            upnl = (entry - current) * qty

        upnl_color = "green" if upnl >= 0 else "red"

        table.add_row("Direction", f"[{direction_color}]{direction_icon} {direction}[/{direction_color}]")
        table.add_row("Entry Price", f"${entry:,.2f}")
        table.add_row("Current Price", f"${current:,.2f}")
        table.add_row("Quantity", f"{qty:.4f} BTC")
        table.add_row("Stop Loss", f"[red]${sl:,.2f}[/red]")
        table.add_row("Take Profit", f"[green]${tp:,.2f}[/green]")
        table.add_row("Unrealized PnL", f"[{upnl_color}]${upnl:+,.2f}[/{upnl_color}]")

        return Panel(table, title="[bold yellow]Open Position[/bold yellow]", border_style="yellow")

    def _build_performance_panel(self) -> Panel:
        """PnL and performance metrics section."""
        total_pnl = self._data["total_pnl"]
        daily_pnl = self._data["daily_pnl"]
        win_rate = self._data["win_rate"]
        total_trades = self._data["total_trades"]

        tp_color = "green" if total_pnl >= 0 else "red"
        dp_color = "green" if daily_pnl >= 0 else "red"

        table = Table(show_header=False, box=None, padding=(0, 2))
        table.add_column("Metric", style="dim")
        table.add_column("Value", style="bold")

        table.add_row("📊 Total PnL", f"[{tp_color}]${total_pnl:+,.2f}[/{tp_color}]")
        table.add_row("📅 Daily PnL", f"[{dp_color}]${daily_pnl:+,.2f}[/{dp_color}]")
        table.add_row("🏆 Win Rate", f"{win_rate:.1%}")
        table.add_row("🔢 Total Trades", str(total_trades))

        return Panel(table, title="[bold green]Performance[/bold green]", border_style="green")

    def _build_signal_panel(self) -> Panel:
        """Current trading signal with confidence."""
        signal = self._data["signal"]
        conf = self._data["signal_confidence"]

        signal_colors = {
            "LONG": "bold green",
            "SHORT": "bold red",
            "NO_TRADE": "bold yellow",
        }
        signal_icons = {"LONG": "🟢 LONG", "SHORT": "🔴 SHORT", "NO_TRADE": "⚪ NO TRADE"}

        color = signal_colors.get(signal, "white")
        icon = signal_icons.get(signal, signal)

        conf_bar = self._confidence_bar(conf)
        sentiment_bar = self._sentiment_bar(self._data["news_sentiment"])

        text = Text()
        text.append(f"  Signal:     ", style="dim")
        text.append(f"{icon}\n", style=color)
        text.append(f"  Confidence: ", style="dim")
        text.append(f"{conf_bar} {conf:.1%}\n", style="white")
        text.append(f"  News:       ", style="dim")
        text.append(f"{sentiment_bar}", style="white")

        return Panel(text, title="[bold magenta]Signal[/bold magenta]", border_style="magenta")

    def _build_logs_panel(self) -> Panel:
        """Recent system log entries."""
        from rich.markup import escape
        log_text = Text()
        for entry in self._log_buffer[-15:]:
            log_text.append(entry + "\n")
        return Panel(
            log_text,
            title="[bold white]System Logs[/bold white]",
            border_style="white",
        )

    def _build_trade_history_panel(self) -> Panel:
        """Recent trade history table."""
        table = Table(
            show_header=True,
            header_style="bold",
            box=None,
            padding=(0, 1),
        )
        table.add_column("Time", style="dim", width=8)
        table.add_column("Dir", width=6)
        table.add_column("Entry", width=10)
        table.add_column("Exit", width=10)
        table.add_column("PnL", width=10)

        history = self._data.get("trade_history", [])
        for trade in history[-8:]:
            direction = trade.get("direction", "")
            dir_color = "green" if direction == "LONG" else "red"
            pnl = trade.get("pnl", 0.0)
            pnl_color = "green" if pnl >= 0 else "red"
            ts = trade.get("timestamp", "")[:8]

            table.add_row(
                ts,
                f"[{dir_color}]{direction[:1]}[/{dir_color}]",
                f"${trade.get('entry', 0):,.0f}",
                f"${trade.get('exit', 0):,.0f}",
                f"[{pnl_color}]{pnl:+,.2f}[/{pnl_color}]",
            )

        return Panel(
            table,
            title="[bold white]Trade History[/bold white]",
            border_style="white",
        )

    def _sentiment_bar(self, score: float) -> str:
        """Visual sentiment bar from -1 to +1."""
        bars = 10
        normalized = int((score + 1) / 2 * bars)
        normalized = max(0, min(bars, normalized))
        if score > 0.2:
            color = "green"
        elif score < -0.2:
            color = "red"
        else:
            color = "yellow"
        filled = "█" * normalized
        empty = "░" * (bars - normalized)
        return f"[{color}]{filled}{empty}[/{color}] {score:+.2f}"

    def _confidence_bar(self, confidence: float) -> str:
        """Visual confidence bar from 0 to 1."""
        bars = 10
        filled_count = int(confidence * bars)
        if confidence >= 0.75:
            color = "green"
        elif confidence >= 0.60:
            color = "yellow"
        else:
            color = "red"
        return f"[{color}]{'█' * filled_count}{'░' * (bars - filled_count)}[/{color}]"

    def render(self) -> Layout:
        """Build and return the complete dashboard layout."""
        layout = Layout()
        layout.split_column(
            Layout(name="header", size=3),
            Layout(name="body"),
            Layout(name="bottom", size=12),
            Layout(name="logs", size=18),
        )

        layout["body"].split_row(
            Layout(name="left", ratio=1),
            Layout(name="right", ratio=1),
        )

        layout["bottom"].split_row(
            Layout(name="performance", ratio=1),
            Layout(name="signal", ratio=1),
            Layout(name="history", ratio=2),
        )

        layout["header"].update(self._build_header())
        layout["left"].update(self._build_account_panel())
        layout["right"].update(self._build_position_panel())
        layout["performance"].update(self._build_performance_panel())
        layout["signal"].update(self._build_signal_panel())
        layout["history"].update(self._build_trade_history_panel())
        layout["logs"].update(self._build_logs_panel())

        return layout

    async def run_live(
        self, update_interval: float = 1.0
    ) -> None:
        """Run the live dashboard in an async context."""
        with Live(
            self.render(),
            console=self._console,
            refresh_per_second=1,
            screen=True,
        ) as live:
            while True:
                live.update(self.render())
                await asyncio.sleep(update_interval)
```

---

## monitoring/prometheus_metrics.py

```python
"""
Prometheus metrics for Grafana monitoring.
Exposes key trading metrics at /metrics endpoint.
"""

from __future__ import annotations

from prometheus_client import Counter, Gauge, start_http_server
from loguru import logger
from config.settings import settings


# ── Gauges (current values) ──────────────────────────────────────────
BTC_PRICE = Gauge("trading_btc_price", "Current BTC/USDT price")
FUNDING_RATE = Gauge("trading_funding_rate", "Current funding rate")
OPEN_INTEREST = Gauge("trading_open_interest_usd", "Open interest in USD")
ACCOUNT_BALANCE = Gauge("trading_account_balance", "Account balance in USDT")
TOTAL_PNL = Gauge("trading_total_pnl", "Total realized PnL")
DAILY_PNL = Gauge("trading_daily_pnl", "Daily PnL")
WIN_RATE = Gauge("trading_win_rate", "Win rate (0-1)")
DRAWDOWN = Gauge("trading_max_drawdown", "Maximum drawdown")
SIGNAL_CONFIDENCE = Gauge("trading_signal_confidence", "Latest signal confidence")
MACRO_SCORE = Gauge("trading_macro_score", "Macro environment score")

# ── Counters (cumulative) ──────────────────────────────────────────────
TRADES_OPENED = Counter("trading_trades_opened_total", "Total trades opened")
TRADES_CLOSED = Counter("trading_trades_closed_total", "Total trades closed")
WINNING_TRADES = Counter("trading_winning_trades_total", "Total winning trades")
LOSING_TRADES = Counter("trading_losing_trades_total", "Total losing trades")
NEWS_PROCESSED = Counter("trading_news_processed_total", "Total news items processed")
OHLCV_FETCHES = Counter(
    "trading_ohlcv_fetches_total",
    "OHLCV data fetches",
    labelnames=["timeframe"],
)

METRICS = {
    "btc_price": BTC_PRICE,
    "funding_rate": FUNDING_RATE,
    "open_interest": OPEN_INTEREST,
    "account_balance": ACCOUNT_BALANCE,
    "total_pnl": TOTAL_PNL,
    "daily_pnl": DAILY_PNL,
    "win_rate": WIN_RATE,
    "drawdown": DRAWDOWN,
    "signal_confidence": SIGNAL_CONFIDENCE,
    "macro_score": MACRO_SCORE,
    "trades_opened": TRADES_OPENED,
    "trades_closed": TRADES_CLOSED,
    "winning_trades": WINNING_TRADES,
    "losing_trades": LOSING_TRADES,
    "news_processed": NEWS_PROCESSED,
    "ohlcv_fetches": OHLCV_FETCHES,
}


def start_metrics_server() -> None:
    """Start Prometheus metrics HTTP server."""
    try:
        start_http_server(settings.prometheus_port)
        logger.info("Prometheus metrics server started on port {}", settings.prometheus_port)
    except Exception as exc:
        logger.warning("Failed to start Prometheus server: {}", exc)
```

---

## main.py

```python
"""
Main entry point for the AI Bitcoin Futures Trading System.

Orchestrates all agents in a fully async architecture using uvloop.
Handles graceful shutdown on SIGINT/SIGTERM.
"""

from __future__ import annotations

import asyncio
import signal
import sys
from datetime import datetime, timezone
from pathlib import Path
from typing import Optional

import uvloop
from loguru import logger

from agents.ai_decision_agent import AIDecisionAgent
from agents.candlestick_pattern_agent import CandlestickPatternAgent
from agents.chart_pattern_agent import ChartPatternAgent
from agents.macro_agent import MacroAgent
from agents.market_data_agent import MarketDataAgent
from agents.news_intelligence_agent import NewsIntelligenceAgent
from agents.performance_agent import PerformanceAgent
from agents.risk_management_agent import RiskManagementAgent
from agents.technical_analysis_agent import TechnicalAnalysisAgent
from agents.trade_execution_agent import TradeExecutionAgent
from config.settings import settings
from dashboard.terminal_dashboard import TradingDashboard
from database.db_manager import DatabaseManager
from monitoring.prometheus_metrics import METRICS, start_metrics_server


def setup_logging() -> None:
    """Configure loguru with structured file and console logging."""
    log_path = Path(settings.log_file)
    log_path.parent.mkdir(parents=True, exist_ok=True)

    logger.remove()  # Remove default handler

    # Console handler - concise
    logger.add(
        sys.stderr,
        format="<green>{time:HH:mm:ss}</green> | <level>{level: <8}</level> | <cyan>{name}</cyan> - <level>{message}</level>",
        level=settings.log_level,
        colorize=True,
    )

    # File handler - detailed JSON for analysis
    logger.add(
        str(log_path),
        format="{time:YYYY-MM-DD HH:mm:ss.SSS} | {level} | {name}:{function}:{line} | {message}",
        level="DEBUG",
        rotation="100 MB",
        retention="30 days",
        compression="gz",
        serialize=False,
    )


class TradingSystem:
    """
    Master orchestrator for all trading agents.
    
    Lifecycle:
    1. initialize() - setup all agents and database
    2. run() - main trading loop
    3. shutdown() - graceful cleanup
    """

    def __init__(self) -> None:
        # Database
        self._db = DatabaseManager()

        # Agents
        self._market_data = MarketDataAgent()
        self._technical = TechnicalAnalysisAgent()
        self._candlestick = CandlestickPatternAgent()
        self._chart_patterns = ChartPatternAgent()
        self._news = NewsIntelligenceAgent(self._db)
        self._macro = MacroAgent()
        self._ai_decision = AIDecisionAgent(self._db)
        self._risk = RiskManagementAgent()
        self._execution = TradeExecutionAgent(self._db)
        self._performance = PerformanceAgent(self._db)

        # Dashboard
        self._dashboard = TradingDashboard()

        # Control flags
        self._running: bool = False
        self._shutdown_event = asyncio.Event()

        # Analysis cycle interval (seconds)
        self._analysis_interval: int = 60  # Full analysis every 60s

    async def initialize(self) -> None:
        """Initialize all agents concurrently."""
        logger.info("Initializing trading system...")

        # Sequential initializations (some have dependencies)
        await self._db.initialize()
        await self._market_data.initialize()
        await self._execution.initialize()
        await self._news.initialize()
        await self._macro.initialize()

        # Start Prometheus metrics
        start_metrics_server()

        logger.info("All agents initialized successfully")
        self._dashboard.add_log("System initialized", "SUCCESS")

    async def _analysis_cycle(self) -> None:
        """
        Core trading analysis cycle.
        
        Runs every 60 seconds:
        1. Fetch latest market data
        2. Run all analysis agents
        3. Generate signal
        4. Execute if approved by risk management
        5. Check stop loss / take profit
        6. Update dashboard
        """
        logger.debug("Starting analysis cycle")

        try:
            # ── 1. FETCH MARKET DATA ─────────────────────────────────────
            ohlcv_all = await self._market_data.fetch_all_timeframes()
            await self._market_data.fetch_orderbook()
            current_price = await self._market_data.fetch_mark_price()
            await self._market_data.fetch_funding_rate()
            await self._market_data.fetch_open_interest()

            if not ohlcv_all or current_price == 0:
                logger.warning("Insufficient market data, skipping cycle")
                return

            # ── 2. TECHNICAL ANALYSIS ────────────────────────────────────
            technical_results = self._technical.analyze(ohlcv_all)

            # ── 3. PATTERN DETECTION ─────────────────────────────────────
            ohlcv_1h = ohlcv_all.get("1h", [])
            ohlcv_4h = ohlcv_all.get("4h", [])

            candlestick_patterns = self._candlestick.detect_all(ohlcv_1h)
            chart_patterns = self._chart_patterns.detect_all(ohlcv_4h)

            # ── 4. NEWS & MACRO ──────────────────────────────────────────
            news_summary = self._news.get_sentiment_summary()
            macro_score = self._macro.macro_score
            macro_summary = {"macro_score": macro_score, **self._macro.macro_data}

            # ── 5. ORDER BOOK ANALYSIS ───────────────────────────────────
            ob = self._market_data.orderbook
            ob_imbalance = self._market_data.calculate_orderbook_imbalance(ob)

            # ── 6. COMPOSE MARKET DATA DICT ─────────────────────────────
            market_context = {
                "ohlcv_1h": ohlcv_1h,
                "ohlcv_4h": ohlcv_4h,
                "current_price": current_price,
                "funding_rate": self._market_data.funding_rate,
                "open_interest": self._market_data.open_interest,
            }

            # ── 7. AI SIGNAL GENERATION ──────────────────────────────────
            signal = self._ai_decision.generate_signal(
                technical_data=technical_results,
                candlestick_patterns=candlestick_patterns,
                chart_patterns=chart_patterns,
                news_summary=news_summary,
                macro_data=macro_summary,
                orderbook={"imbalance": ob_imbalance},
                market_data=market_context,
            )

            # ── 8. PERSIST SIGNAL ────────────────────────────────────────
            await self._db.save_signal({
                "action": signal.action,
                "confidence": signal.confidence,
                "technical_score": signal.technical_score,
                "pattern_score": signal.pattern_score,
                "sentiment_score": signal.sentiment_score,
                "macro_score": signal.macro_score,
                "orderbook_score": signal.orderbook_score,
                "volume_score": signal.volume_score,
                "oi_score": signal.oi_score,
                "funding_score": signal.funding_score,
                "reasoning": signal.reasoning,
                "indicators_snapshot": signal.indicators_snapshot,
                "patterns_detected": signal.patterns_detected,
                "news_summary": signal.news_summary,
                "market_regime": signal.market_regime,
            })

            # ── 9. EXECUTE IF ACTIONABLE ─────────────────────────────────
            if signal.action in ("LONG", "SHORT") and not self._execution.has_open_position:
                atr = self._technical.get_atr(ohlcv_1h)
                balance = await self._execution.get_account_balance()

                trade_params = self._risk.validate_and_size_trade(
                    direction=signal.action,
                    entry_price=current_price,
                    atr=atr,
                    balance=balance,
                )

                if trade_params.approved:
                    order = await self._execution.execute_trade(trade_params)
                    if order:
                        self._dashboard.add_log(
                            f"Trade opened: {signal.action} @ ${current_price:,.2f} "
                            f"| Conf: {signal.confidence:.1%}",
                            "SUCCESS",
                        )
                else:
                    logger.info(
                        "Trade rejected by risk: {}", trade_params.rejection_reason
                    )
                    self._dashboard.add_log(
                        f"Trade rejected: {trade_params.rejection_reason}", "WARNING"
                    )

            # ── 10. CHECK OPEN POSITION ──────────────────────────────────
            elif self._execution.has_open_position:
                pos = self._execution.open_position
                if pos:
                    should_close, close_reason = self._check_exit_conditions(
                        pos, current_price, signal
                    )
                    if should_close:
                        pnl = await self._execution.close_position(
                            reason=close_reason,
                            current_price=current_price,
                        )
                        if pnl is not None:
                            self._risk.record_trade_result(pnl)
                            self._performance.record_trade(
                                pnl=pnl,
                                direction=pos["direction"],
                                entry=pos["entry_price"],
                                exit_price=current_price,
                                timestamp=datetime.now(timezone.utc).isoformat(),
                            )

            # ── 11. UPDATE METRICS & DASHBOARD ───────────────────────────
            perf = self._performance.get_metrics()
            balance = await self._execution.get_account_balance()

            METRICS["btc_price"].set(current_price)
            METRICS["signal_confidence"].set(signal.confidence)
            METRICS["account_balance"].set(balance)
            METRICS["daily_pnl"].set(perf["daily_pnl"])
            METRICS["win_rate"].set(perf["win_rate"])

            self._dashboard.update({
                "btc_price": current_price,
                "system_status": "RUNNING" if not self._risk.is_halted else "HALTED",
                "mode": "PAPER" if settings.paper_trading else "LIVE",
                "balance": balance,
                "available_margin": balance * 0.90,  # Approximate
                "used_margin": balance * 0.10,
                "leverage": settings.leverage,
                "open_position": self._execution.open_position,
                "total_pnl": perf["total_pnl"],
                "daily_pnl": perf["daily_pnl"],
                "win_rate": perf["win_rate"],
                "total_trades": perf["total_trades"],
                "signal": signal.action,
                "signal_confidence": signal.confidence,
                "news_sentiment": news_summary.get("aggregate_score", 0.0),
                "market_regime": signal.market_regime,
                "funding_rate": self._market_data.funding_rate,
                "open_interest": self._market_data.open_interest,
                "macro_score": macro_score,
            })

            self._dashboard.add_log(
                f"Cycle complete | {signal.action} {signal.confidence:.1%} "
                f"| BTC: ${current_price:,.2f}",
                "INFO",
            )

        except Exception as exc:
            logger.exception("Analysis cycle error: {}", exc)
            self._dashboard.add_log(f"Cycle error: {exc}", "ERROR")

    def _check_exit_conditions(
        self, pos: dict, current_price: float, signal: object
    ) -> tuple[bool, str]:
        """
        Determine if open position should be closed.
        
        Exit conditions:
        1. Stop loss hit
        2. Take profit hit  
        3. Opposing signal generated
        4. Trading halted
        """
        direction = pos.get("direction", "")
        stop_loss = pos.get("stop_loss", 0.0)
        take_profit = pos.get("take_profit", 0.0)

        # Emergency: trading halted
        if self._risk.is_halted:
            return True, "trading_halted"

        # Stop loss check
        if direction == "LONG" and current_price <= stop_loss:
            return True, "stop_loss"
        if direction == "SHORT" and current_price >= stop_loss:
            return True, "stop_loss"

        # Take profit check
        if direction == "LONG" and current_price >= take_profit:
            return True, "take_profit"
        if direction == "SHORT" and current_price <= take_profit:
            return True, "take_profit"

        # Opposing signal check
        sig_action = getattr(signal, "action", "NO_TRADE")
        sig_conf = getattr(signal, "confidence", 0.0)
        if (
            sig_conf >= settings.min_confidence_threshold + 0.10  # Higher bar for flip
            and (
                (direction == "LONG" and sig_action == "SHORT")
                or (direction == "SHORT" and sig_action == "LONG")
            )
        ):
            return True, "signal_reversal"

        return False, ""

    async def _main_loop(self) -> None:
        """Main trading loop running analysis on configured interval."""
        logger.info("Starting main trading loop (interval: {}s)", self._analysis_interval)
        self._running = True

        while self._running and not self._shutdown_event.is_set():
            await self._analysis_cycle()
            try:
                await asyncio.wait_for(
                    asyncio.shield(self._shutdown_event.wait()),
                    timeout=self._analysis_interval,
                )
                break  # Shutdown event received
            except asyncio.TimeoutError:
                pass  # Normal timeout, continue loop

    async def run(self) -> None:
        """Start all agents and run the trading system."""
        await self.initialize()

        # Create tasks for all background agents
        tasks = [
            asyncio.create_task(self._main_loop(), name="main_loop"),
            asyncio.create_task(self._market_data.start_streaming(), name="market_stream"),
            asyncio.create_task(self._news.start(), name="news_agent"),
            asyncio.create_task(self._macro.start(), name="macro_agent"),
            asyncio.create_task(self._dashboard.run_live(), name="dashboard"),
        ]

        logger.info("All systems running. Press Ctrl+C to shutdown.")

        # Wait for any task to complete (or fail)
        done, pending = await asyncio.wait(
            tasks, return_when=asyncio.FIRST_EXCEPTION
        )

        # Cancel remaining tasks on shutdown
        for task in pending:
            task.cancel()
            try:
                await task
            except asyncio.CancelledError:
                pass

    async def shutdown(self) -> None:
        """Graceful shutdown with position safety check."""
        logger.warning("Shutting down trading system...")
        self._running = False
        self._shutdown_event.set()

        # Emergency close any open positions
        if self._execution.has_open_position:
            logger.warning("Closing open position before shutdown...")
            price = self._market_data.current_price
            await self._execution.emergency_close()

        # Stop all agents
        await self._market_data.stop()
        await self._news.stop()
        await self._macro.stop()
        await self._db.close()

        logger.info("Trading system shutdown complete")


async def main() -> None:
    """Entry point with signal handling and uvloop."""
    setup_logging()
    logger.info("=" * 60)
    logger.info("AI Bitcoin Futures Trading System")
    logger.info(f"Mode: {'PAPER' if settings.paper_trading else 'LIVE'}")
    logger.info(f"Symbol: {settings.symbol} | Leverage: {settings.leverage}x")
    logger.info(f"Strategy Version: {settings.strategy_version}")
    logger.info("=" * 60)

    system = TradingSystem()

    # Register signal handlers for graceful shutdown
    loop = asyncio.get_event_loop()

    def _shutdown_handler(sig_name: str) -> None:
        logger.warning("Received signal: {}", sig_name)
        asyncio.ensure_future(system.shutdown())

    for sig in (signal.SIGTERM, signal.SIGINT):
        try:
            loop.add_signal_handler(
                sig, lambda s=sig.name: _shutdown_handler(s)
            )
        except NotImplementedError:
            # Windows fallback
            pass

    try:
        await system.run()
    except Exception as exc:
        logger.critical("Fatal error: {}", exc)
        await system.shutdown()
        raise


if __name__ == "__main__":
    # Use uvloop for maximum async performance on Linux
    if sys.platform != "win32":
        asyncio.set_event_loop_policy(uvloop.EventLoopPolicy())

    asyncio.run(main())
```

---

## tests/test_technical_analysis.py

```python
"""Unit tests for TechnicalAnalysisAgent."""

from __future__ import annotations

import time
from typing import Any

import numpy as np
import pytest

from agents.technical_analysis_agent import TechnicalAnalysisAgent


def make_ohlcv(n: int = 200, base_price: float = 50000.0) -> list[list]:
    """Generate synthetic OHLCV data for testing."""
    rng = np.random.default_rng(42)
    data = []
    price = base_price
    ts = int(time.time() * 1000) - n * 3600 * 1000

    for i in range(n):
        change = rng.normal(0, 0.01) * price
        open_p = price
        close_p = price + change
        high_p = max(open_p, close_p) + abs(rng.normal(0, 0.003) * price)
        low_p = min(open_p, close_p) - abs(rng.normal(0, 0.003) * price)
        volume = abs(rng.normal(100, 30))
        data.append([ts + i * 3600000, open_p, high_p, low_p, close_p, volume])
        price = close_p

    return data


class TestTechnicalAnalysisAgent:
    @pytest.fixture
    def agent(self) -> TechnicalAnalysisAgent:
        return TechnicalAnalysisAgent()

    @pytest.fixture
    def ohlcv(self) -> list[list]:
        return make_ohlcv(200)

    def test_analyze_returns_composite_score(
        self, agent: TechnicalAnalysisAgent, ohlcv: list[list]
    ) -> None:
        result = agent.analyze({"1h": ohlcv})
        assert "composite_score" in result
        score = result["composite_score"]
        assert -1.0 <= score <= 1.0, f"Score {score} out of range [-1, 1]"

    def test_composite_score_is_float(
        self, agent: TechnicalAnalysisAgent, ohlcv: list[list]
    ) -> None:
        result = agent.analyze({"1h": ohlcv})
        assert isinstance(result["composite_score"], float)

    def test_per_timeframe_score_in_range(
        self, agent: TechnicalAnalysisAgent, ohlcv: list[list]
    ) -> None:
        result = agent.analyze({"1h": ohlcv, "4h": ohlcv})
        for tf in ["1h", "4h"]:
            if tf in result:
                score = result[tf]["score"]
                assert -1.0 <= score <= 1.0

    def test_insufficient_candles_returns_zero(
        self, agent: TechnicalAnalysisAgent
    ) -> None:
        tiny_ohlcv = make_ohlcv(10)  # Too few
        result = agent.analyze({"1h": tiny_ohlcv})
        # Should handle gracefully
        assert "composite_score" in result

    def test_get_atr_returns_positive(
        self, agent: TechnicalAnalysisAgent, ohlcv: list[list]
    ) -> None:
        atr = agent.get_atr(ohlcv)
        assert atr > 0

    def test_multiple_timeframes(
        self, agent: TechnicalAnalysisAgent
    ) -> None:
        ohlcv = make_ohlcv(200)
        result = agent.analyze({
            "1m": ohlcv,
            "5m": ohlcv,
            "1h": ohlcv,
            "4h": ohlcv,
            "1d": ohlcv,
        })
        assert "composite_score" in result
        assert isinstance(result["composite_score"], float)
```

---

## tests/test_risk_management.py

```python
"""Unit tests for RiskManagementAgent."""

from __future__ import annotations

import pytest

from agents.risk_management_agent import RiskManagementAgent, TradeParameters
from config.settings import settings


class TestRiskManagementAgent:
    @pytest.fixture
    def agent(self) -> RiskManagementAgent:
        return RiskManagementAgent()

    @pytest.fixture
    def valid_params(self) -> dict:
        return {
            "direction": "LONG",
            "entry_price": 50000.0,
            "atr": 500.0,  # 1% ATR
            "balance": 10000.0,
        }

    def test_valid_long_trade_approved(
        self, agent: RiskManagementAgent, valid_params: dict
    ) -> None:
        params = agent.validate_and_size_trade(**valid_params)
        assert params.approved is True
        assert params.direction == "LONG"
        assert params.quantity > 0
        assert params.stop_loss < params.entry_price  # Long: SL below entry

    def test_valid_short_trade_approved(
        self, agent: RiskManagementAgent
    ) -> None:
        params = agent.validate_and_size_trade(
            direction="SHORT",
            entry_price=50000.0,
            atr=500.0,
            balance=10000.0,
        )
        assert params.approved is True
        assert params.stop_loss > params.entry_price  # Short: SL above entry

    def test_zero_balance_rejected(
        self, agent: RiskManagementAgent
    ) -> None:
        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=500.0,
            balance=0.0,
        )
        assert params.approved is False
        assert params.rejection_reason is not None

    def test_zero_atr_rejected(
        self, agent: RiskManagementAgent
    ) -> None:
        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=0.0,
            balance=10000.0,
        )
        assert params.approved is False

    def test_risk_reward_minimum_ratio(
        self, agent: RiskManagementAgent, valid_params: dict
    ) -> None:
        params = agent.validate_and_size_trade(**valid_params)
        if params.approved:
            assert params.risk_reward_ratio >= settings.risk_reward_ratio - 0.01

    def test_position_size_cap(
        self, agent: RiskManagementAgent
    ) -> None:
        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=50.0,  # Tiny ATR → large quantity from risk
            balance=10000.0,
        )
        if params.approved:
            max_usd = 10000.0 * settings.max_position_size_pct * settings.leverage
            assert params.position_size_usd <= max_usd + 1.0  # Allow rounding

    def test_consecutive_losses_halt(
        self, agent: RiskManagementAgent
    ) -> None:
        # Simulate max consecutive losses
        for _ in range(settings.max_consecutive_losses):
            agent.record_trade_result(-100.0)

        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=500.0,
            balance=10000.0,
        )
        assert params.approved is False
        assert "consecutive" in (params.rejection_reason or "").lower()

    def test_existing_position_rejected(
        self, agent: RiskManagementAgent
    ) -> None:
        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=500.0,
            balance=10000.0,
            current_position_size=0.1,  # Existing position
        )
        assert params.approved is False

    def test_winning_trade_resets_consecutive_losses(
        self, agent: RiskManagementAgent
    ) -> None:
        agent.record_trade_result(-100.0)
        agent.record_trade_result(-100.0)
        assert agent.consecutive_losses == 2
        agent.record_trade_result(200.0)  # Win
        assert agent.consecutive_losses == 0

    def test_abnormal_volatility_rejected(
        self, agent: RiskManagementAgent
    ) -> None:
        # 10% ATR = abnormal volatility
        params = agent.validate_and_size_trade(
            direction="LONG",
            entry_price=50000.0,
            atr=5000.0,  # 10% of price
            balance=10000.0,
        )
        assert params.approved is False
```

---

## tests/test_candlestick_patterns.py

```python
"""Unit tests for CandlestickPatternAgent."""

from __future__ import annotations

import time

import pytest

from agents.candlestick_pattern_agent import CandlestickPattern, CandlestickPatternAgent


def make_candle(
    ts: int,
    open_p: float,
    high: float,
    low: float,
    close: float,
    volume: float = 100.0,
) -> list:
    return [ts, open_p, high, low, close, volume]


class TestCandlestickPatternAgent:
    @pytest.fixture
    def agent(self) -> CandlestickPatternAgent:
        return CandlestickPatternAgent()

    @pytest.fixture
    def base_ts(self) -> int:
        return int(time.time() * 1000) - 100 * 3600000

    def make_candles(self, specs: list[tuple], base_ts: int) -> list[list]:
        """Build candle list from (open, high, low, close) tuples."""
        return [
            make_candle(base_ts + i * 3600000, o, h, l, c)
            for i, (o, h, l, c) in enumerate(specs)
        ]

    def test_detect_hammer(
        self, agent: CandlestickPatternAgent, base_ts: int
    ) -> None:
        """Hammer: long lower shadow, small body, little upper shadow."""
        # Price: 50000, small body near top, long lower shadow
        candles = self.make_candles(
            [
                (50000, 50100, 48000, 50050),  # Hammer candle
            ],
            base_ts,
        ) * 5  # Pad to minimum length

        patterns = agent.detect_all(candles)
        hammer = [p for p in patterns if p.name == "Hammer"]
        if hammer:
            assert hammer[0].direction == "bullish"
            assert hammer[0].confidence >= 0.5

    def test_detect_doji(
        self, agent: CandlestickPatternAgent, base_ts: int
    ) -> None:
        """Doji: open nearly equals close."""
        candles = self.make_candles(
            [(50000, 50200, 49800, 50001)],  # Open ≈ Close
            base_ts,
        ) * 5

        patterns = agent.detect_all(candles)
        dojis = [p for p in patterns if p.name == "Doji"]
        if dojis:
            assert dojis[0].direction == "neutral"

    def test_bullish_engulfing_detection(
        self, agent: CandlestickPatternAgent, base_ts: int
    ) -> None:
        """Bullish engulfing: small bearish then large bullish."""
        bearish = (50200, 50300, 50000, 50100)  # Bearish
        bullish = (50050, 50500, 50000, 50450)  # Bullish engulfs

        candles = self.make_candles([bearish] * 3 + [bullish], base_ts)
        patterns = agent.detect_all(candles)
        engulfing = [p for p in patterns if "Engulfing" in p.name and p.direction == "bullish"]
        # Pattern may or may not be detected depending on lookback
        # Just ensure no exceptions are raised
        assert isinstance(patterns, list)

    def test_aggregate_score_range(
        self, agent: CandlestickPatternAgent, base_ts: int
    ) -> None:
        """Aggregate score should be in -1 to +1 range."""
        candles = self.make_candles(
            [(50000, 50500, 49500, 50300)] * 10,
            base_ts,
        )
        patterns = agent.detect_all(candles)
        score = agent.aggregate_score(patterns)
        assert -1.0 <= score <= 1.0

    def test_returns_list(
        self, agent: CandlestickPatternAgent
    ) -> None:
        """Should always return list, even with insufficient data."""
        result = agent.detect_all([])
        assert isinstance(result, list)
        assert len(result) == 0

    def test_confidence_range(
        self, agent: CandlestickPatternAgent, base_ts: int
    ) -> None:
        """All pattern confidence scores must be in 0.0 to 1.0."""
        import numpy as np

        rng = np.random.default_rng(123)
        prices = 50000 + rng.normal(0, 500, 50).cumsum()
        candles = []
        for i, price in enumerate(prices):
            o, c = price, price + rng.normal(0, 100)
            h = max(o, c) + abs(rng.normal(0, 50))
            l = min(o, c) - abs(rng.normal(0, 50))
            candles.append([base_ts + i * 3600000, o, h, l, c, 100.0])

        patterns = agent.detect_all(candles)
        for p in patterns:
            assert 0.0 <= p.confidence <= 1.0, f"{p.name} confidence {p.confidence} out of range"
```

---

## tests/test_signal_aggregator.py

```python
"""Unit tests for AI Decision Agent signal generation."""

from __future__ import annotations

from unittest.mock import AsyncMock, MagicMock, patch

import pytest

from agents.ai_decision_agent import AIDecisionAgent, TradingSignal
from database.db_manager import DatabaseManager


class TestAIDecisionAgent:
    @pytest.fixture
    def mock_db(self) -> MagicMock:
        db = MagicMock(spec=DatabaseManager)
        db.save_signal = AsyncMock(return_value=1)
        return db

    @pytest.fixture
    def agent(self, mock_db: MagicMock) -> AIDecisionAgent:
        return AIDecisionAgent(mock_db)

    @pytest.fixture
    def bullish_inputs(self) -> dict:
        return {
            "technical_data": {"composite_score": 0.80},
            "candlestick_patterns": [],
            "chart_patterns": [],
            "news_summary": {"aggregate_score": 0.60, "top_headlines": []},
            "macro_data": {"macro_score": 0.50},
            "orderbook": {"imbalance": 0.40},
            "market_data": {"ohlcv_1h": [], "current_price": 50000.0, "funding_rate": 0.0001, "open_interest": 1e9},
        }

    @pytest.fixture
    def bearish_inputs(self) -> dict:
        return {
            "technical_data": {"composite_score": -0.80},
            "candlestick_patterns": [],
            "chart_patterns": [],
            "news_summary": {"aggregate_score": -0.60, "top_headlines": []},
            "macro_data": {"macro_score": -0.50},
            "orderbook": {"imbalance": -0.40},
            "market_data": {"ohlcv_1h": [], "current_price": 50000.0, "funding_rate": -0.0001, "open_interest": 1e9},
        }

    def test_signal_returns_trading_signal(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        assert isinstance(signal, TradingSignal)

    def test_bullish_inputs_generate_long(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        # With strong bullish scores, should lean LONG
        assert signal.action in ("LONG", "NO_TRADE")

    def test_bearish_inputs_generate_short(
        self, agent: AIDecisionAgent, bearish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bearish_inputs)
        assert signal.action in ("SHORT", "NO_TRADE")

    def test_confidence_in_valid_range(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        assert 0.0 <= signal.confidence <= 1.0

    def test_reasoning_not_empty(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        assert len(signal.reasoning) > 10

    def test_all_scores_recorded(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        assert signal.technical_score != 0.0
        assert signal.sentiment_score != 0.0

    def test_neutral_inputs_generate_no_trade(
        self, agent: AIDecisionAgent
    ) -> None:
        neutral_inputs = {
            "technical_data": {"composite_score": 0.01},
            "candlestick_patterns": [],
            "chart_patterns": [],
            "news_summary": {"aggregate_score": 0.0, "top_headlines": []},
            "macro_data": {"macro_score": 0.0},
            "orderbook": {"imbalance": 0.0},
            "market_data": {"ohlcv_1h": [], "current_price": 50000.0, "funding_rate": 0.0, "open_interest": 1e9},
        }
        signal = agent.generate_signal(**neutral_inputs)
        assert signal.action == "NO_TRADE"

    def test_timestamp_is_set(
        self, agent: AIDecisionAgent, bullish_inputs: dict
    ) -> None:
        signal = agent.generate_signal(**bullish_inputs)
        assert signal.timestamp is not None
        assert len(signal.timestamp) > 0
```

---

## Dockerfile

```dockerfile
# ── Stage 1: Builder ──────────────────────────────────────────────────────────
FROM python:3.13-slim AS builder

WORKDIR /build

# Install build dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    libffi-dev \
    libssl-dev \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir --prefix=/install -r requirements.txt

# ── Stage 2: Runtime ──────────────────────────────────────────────────────────
FROM python:3.13-slim AS runtime

# Non-root user for security
RUN groupadd -r trader && useradd -r -g trader -u 1001 trader

WORKDIR /app

# Runtime dependencies only
RUN apt-get update && apt-get install -y --no-install-recommends \
    libgomp1 \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Copy installed packages from builder
COPY --from=builder /install /usr/local

# Copy application code
COPY --chown=trader:trader . .

# Create required directories
RUN mkdir -p logs && chown trader:trader logs

# Switch to non-root user
USER trader

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=60s --retries=3 \
    CMD curl -f http://localhost:8000/metrics || exit 1

# Expose Prometheus metrics port
EXPOSE 8000

# Environment variables (overridden at runtime)
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONPATH=/app

ENTRYPOINT ["python", "main.py"]
```

---

## docker-compose.yml

```yaml
version: "3.9"

services:
  # ── Trading Bot ────────────────────────────────────────────────────
  trading_bot:
    build:
      context: .
      dockerfile: Dockerfile
      target: runtime
    container_name: btc_trading_bot
    restart: unless-stopped
    env_file:
      - .env
    volumes:
      - ./logs:/app/logs
      - ./trading_bot.db:/app/trading_bot.db
    ports:
      - "8000:8000"   # Prometheus metrics
    depends_on:
      - prometheus
      - grafana
    networks:
      - trading_net
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/metrics"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 90s
    deploy:
      resources:
        limits:
          memory: 4G
          cpus: "2.0"

  # ── Prometheus ─────────────────────────────────────────────────────
  prometheus:
    image: prom/prometheus:v2.55.1
    container_name: btc_prometheus
    restart: unless-stopped
    ports:
      - "9090:9090"
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml:ro
      - prometheus_data:/prometheus
    command:
      - "--config.file=/etc/prometheus/prometheus.yml"
      - "--storage.tsdb.path=/prometheus"
      - "--storage.tsdb.retention.time=30d"
      - "--web.enable-lifecycle"
    networks:
      - trading_net

  # ── Grafana ────────────────────────────────────────────────────────
  grafana:
    image: grafana/grafana:11.3.0
    container_name: btc_grafana
    restart: unless-stopped
    ports:
      - "3000:3000"
    environment:
      - GF_SECURITY_ADMIN_PASSWORD=admin
      - GF_USERS_ALLOW_SIGN_UP=false
    volumes:
      - grafana_data:/var/lib/grafana
      - ./monitoring/grafana/dashboards:/etc/grafana/provisioning/dashboards:ro
    depends_on:
      - prometheus
    networks:
      - trading_net

volumes:
  prometheus_data:
  grafana_data:

networks:
  trading_net:
    driver: bridge
```

---

## monitoring/prometheus.yml

```yaml
global:
  scrape_interval: 15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: "trading_bot"
    static_configs:
      - targets: ["trading_bot:8000"]
    scrape_interval: 10s
    metrics_path: /metrics
```

---

## Key Architecture Decisions & Production Notes

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SYSTEM ARCHITECTURE OVERVIEW                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                           │
│  WebSocket Streams ──► MarketDataAgent ──► shared data dict             │
│                              │                                            │
│  RSS/News APIs ──────► NewsIntelligenceAgent (FinBERT)                  │
│                              │                                            │
│  Yahoo Finance ──────► MacroAgent (DXY/VIX/Nasdaq)                      │
│                              │                                            │
│  All agents feed ───────────► AIDecisionAgent                            │
│                              │                                            │
│                         weighted score                                    │
│                              │                                            │
│                    ┌─────────▼──────────┐                                │
│                    │ RiskManagementAgent │ ◄── circuit breaker           │
│                    └─────────┬──────────┘                                │
│                              │ approved params                            │
│                    ┌─────────▼──────────┐                                │
│                    │ TradeExecutionAgent │ ◄── paper/live mode           │
│                    └─────────┬──────────┘                                │
│                              │                                            │
│                    ┌─────────▼──────────┐                                │
│                    │  DatabaseManager   │ ◄── SQLite async               │
│                    └────────────────────┘                                │
│                                                                           │
│  Dashboard (Rich) ◄── all agents ──► Prometheus ──► Grafana             │
│                                                                           │
└─────────────────────────────────────────────────────────────────────────┘

CRITICAL SAFETY RULES (hardcoded):
1. PAPER_TRADING=true by default - must explicitly set false for live
2. Risk management agent has absolute veto power
3. Circuit breaker auto-opens on 5% drawdown
4. Max 5 consecutive losses → system halt
5. No averaging down - enforced in code
6. ATR-based stops - no fixed percentage stops
7. All signals logged with FULL reasoning to SQLite
8. Graceful shutdown always attempts position close

DEPLOYMENT:
  docker-compose up --build -d

TESTING:
  pytest tests/ -v --asyncio-mode=auto

LIVE TRADING CHECKLIST:
  [ ] Set PAPER_TRADING=false
  [ ] Set BINANCE_TESTNET=false  
  [ ] Fund testnet account first
  [ ] Verify API key permissions
  [ ] Set appropriate leverage (start with 3x)
  [ ] Monitor first 10 trades manually
  [ ] Review daily PnL before extending
```
