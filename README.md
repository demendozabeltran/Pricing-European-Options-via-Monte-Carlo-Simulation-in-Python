PRICING EUROPEAN OPTIONS VIA MONTE CARLO SIMULATIONS

This project uses a million simulations to calculate the call and put prices of European options.
The backbone of the project is Geometric Brownian Motion and the Box-Muller transform. 
This project uses Monte Carlo simulations to give the exact payoff of an option 
by taking an average of thousands or millions of simulations.

To generate gaussian random numbers, or random numbers in a normal distribution, 
I used a variation of the Box-Muller transform called the Marsaglia polar method. 
The reason that the Box-Muller transform is not great for this particular project is because 
it calls on trig functions which are more time-expensive than the Marsaglia polar method.

The Marsaglia polar method works by generating random values within a two dimensional square with side-lengths of two. 
Then we create a circle with radius 1, and if there are points that are in the square but not in the circle those points will be thrown out. 
The circle is then stretched out along the X axis to create a normal distribution.

To calculate the call and put prices, you only need the equation:

Price = Initial Price * e ^ ((rate - (½)volatility) time + volatility √(time) * Gaussian

However, for calls, you only want to include a simulation in the total payout if the returning price is 
greater than the strike price.

On the other hand, for put options you only want to add to the total payout if the strike price is greater than the 
returning price, as that is how you would make money.

A helper function is necessary to make sure that the value is greater than 0. 
If the value is greater than 0 it will return the value. If it is less it will return 0. 
By returning 0 we are also demonstrating the contract holders right to not purchase or sell any of the underlying 
assets within the option.

All variables at the end can be changed accordingly and are arbitrarily chosen for testing and demonstration.
