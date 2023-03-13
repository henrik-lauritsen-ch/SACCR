# SACCR
Function to be applied for SACCR EAD Calculation according to bcbs279

The implementation assumes that the calculation currency is CHF and that all notional amounts and prices are already in this currency.

The SACCR method is basically a combination of "sum-product" and a few "group by" statements. In order to do correct aggregation so called "hedge sets" are build. For FX poisitions there are a few points to take into consideration.

FX Hedge Sets are build for a specific combination of two currencies. As an examplpe for FX derivatives involving EUR and USD this can either be EURUSD or USDEUR (free choice). Now a financial institution may have a position in EURUSD where it buys EUR for USD and another position where it buys USD for EUR. 
  
  1. First step: select EURUSD as Hedge set (or USDEUR if preferred)

  2. Second step: find delta of the forward positions. For the buy EUR, sell USD this is seen from a EURUSD point of view a "buy" i.e. delta would be 1.0. The Buy USD, Sell EUR is considered a "sell" seen from a EURUSD point of view, which means that the delta should be -1.0

In case there are FX option under a netting set switching the cross around from USDEUR to EURUSD would not be done through the buy/sell sign but re-defining a call to a put (or the other way around)


