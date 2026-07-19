Time Series: Forecasting on ordered data.
Foremost, we begin with plotting our time series to identify what we are working with. Our data, could be additive or multplicative(real data- mmm). 
Our dataset is additive — the seasonal swing stays ±25 all year; the envelope is a flat ribbon, no funnel.
Our dataset can be described by 3 known components which define common or daily occurrences e.g. SALES and TEMPERATURE. They include;
a. TREND. - a pattern that our dataset follows.
b. SEASONALITY. - Repetition. The sine is how we generated it.
c. NOISE - Unexplained natural occurrences. Uncontrollable.

These are easily observable with the seasonal decomposition important during data exploration.
Once data is farmiliar: we need to fit baseline models, and compare them to other industry standard models.

General rule for ordered data, we never split randomly:
the chronological split.
The foundational rule of the whole project — train on past, test on future, no shuffling, because random splits leak the future

Baseline models:
1. Plain naive - first model, scoring an MAE of 20.8, it assumed tomorrow will be exactly like today.Doesn't look behind the scenes for the trend and sine wave.
2. Seasonal naive - second model fitted, scored an MAE of 20.2, assumes last 7 days(our wave cycle) will match the future. although it captures, the seasonality, it missed the trend but a better improvement to the plain naive.

MODELS:
models with one recipe and 3 integer dials(ARIMA(p,d,q), which means:
AR(Auto Regressive)- today depends on the last p days. 
I(Integrated) - Difference away the trend.(d-dial)
MA(Moving average) - The model corrects itself from previous errors.(q-dial)

Results from each table are as:
Model			MAE
Plain naive		20.80
Seasonal naive		20.23
ARIMA(1,1,1)		20.80
ARIMA(7,1,0)		17.69
SARIMA(1,1,1)(1,1,1,7)	12.11
Noise floor		~12

ARIMA performs like the plain naive because: 
- It is blind to seasonality.
- Its mechanism: corrections feed on recent actual values, and past a few forecast steps there are none- so the forecast collapses into a flat line at the last known level, which is literally the naive forecast.
ARIMA tuned, picks the weekly cycle and attempts the wave only to flatten at the end, when it starts repeating itself from its own data.
enters SARIMA, with a dial(s) for seasonality where we defined the seasonality period of our wave cycle to 7, it picked up the trend and seasonality and reached the noise floor of 12.

Note: we only know the floor because we built the data. On real data the floor is invisible — you never know if your model is done.