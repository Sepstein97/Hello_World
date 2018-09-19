import quantopian.pipeline
from quantopian.research import prices, symbols
import pandas as pd
aapl_close = prices(
    assets=symbols('AAPL'),
    start='2013-01-01',
    end='2016-01-01',)
aapl_sma20 = aapl_close.rolling(20).mean()
aapl_sma50 = aapl_close.rolling(50).mean()
pd.Dataframe({
    'AAPL': aapl_close,
    'SMA20': aapl_sma20,
    'SMA50': aapl_sma50
}).plot(
    title = 'AAPL Close Price / SMA Crossover'
);
