# Money Market Basis Curve

A money market basis swap is an exchange of two floating rate notes referencing two different rate indices (indices can differ just by the length of underlying term, like USD 3 Month LIBOR versus USD 1 Month LIBOR, or by nature altogether, like USD 3 Month LIBOR versus USD 3 Month CD). 

Basis spreads can be applied to the indices (typically, to just one of them, the other being considered the reference index). The principals of the notes are denominated in the same currency (in our example, USD). Principals may be paid/received at maturity, or not (this last case is typical for money market basis swaps). (This contrasts with cross-currency basis swap situation where principals do change hands both at the effective date and maturity date, with principals related by a fixed contractual FX rate.

Here, we re-review interest rate constructions needed to value typical swaps in (single currency) money market basis context. One of the indices is assumed to be the reference (benchmark) index (for example, USD 3 Month LIBOR). 

Typically, this would be the index rate at which funding (and collateralization) would be done (for example, in a USD 1 Month LIBOR/ USD 3 Month LIBOR basis swap, USD 3 Month LIBOR would be the reference index). We refer to the other index as the nonreference index (in our example, USD 1 Month LIBOR is the non-reference index). 

Money market basis swap is the main traded contract we are using in this context. From liquidly quoted (standard) money market basis swap par spreads and independently existent interest rate curves, one needs to build four curves that are used for index rate forecasting and cash-flow discounting for each of the two legs that make up a typical money market basis swap. 

It is market practice to first make a series of assumptions and then build these curves so that the input money market basis swap is priced at par under them (the bootstrap methodology is explained in detail in the main text). On the reference index side, the original interest rate curve (in our example, USD 3 Month LIBOR curve) is used for both forecasting and discounting. 

This assumption usually renders the reference index leg price close to par (it may not necessarily be at par, especially when the first index calculation date is today or earlier than today and one allows usage of historical index reset). 

On the non-reference index side, one assumes that the original reference interest rate curve (in our example, USD 3 Month LIBOR curve) can be used for discounting. As one needs to apply a basis spread to the non-reference index rate, a new forecasting curve (in our example, a new USD 1 Month LIBOR curve to be used for computing 1 Month forward rates) must be build in order to keep the whole basis swap at par. 

The new non-reference zero curve is viewed as the sum between the original reference zero curve and a zero spread curve. The objective of the bootstrap algorithm is to find this non-reference zero spread curve.

The traditional approach for building non-reference interest rate curves can be used to price typical money-market basis swap deals. This methodology could introduce inconsistencies. Discounting a cash flow with different curves just because different products generate them is undesirable and the discrepancies should be controlled. 

A solution that tries to address this inconsistency issue is proposed. The main idea is to produce two new curves (one for forecasting and one for discounting) so that both basis swaps and interest rate swaps are correctly re-priced in the same time. 

Assuming there is no interest in pursuing a different solution in short term (thus eliminating more model risks), the classical approach can be considered reasonable. 

Let us assume that we are given a discount factor curve PA (t, T), which we use to discount the A cash flow (such as bond coupon payment schedule, and a discount factor curve PB (t, T), which we use to discount the B cash flow. Note that these two discounting curves are not assumed to be equal! 

Reference:

https://finpricing.com/FinPricing-ProductBrochure.pdf
