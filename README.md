# targeted_beta
Fetched data from Yahoo Finance by using python api, performed sql statement in python through sqlalchemy, constructed portfolio with the targeted beta.

# Outline
In this project, we fetched the stock data of the given 3k cusips, evaluated their betas using CAPM model, constructed a portfolio which has the targeted beta, and calculated the return of the portfolio in the next year.

## Table Design

Designed three table to store stock data, stock return data, and the regression result.

Table 1

    table name: BarValues
    
        Ticker - char 6
        Company Name - Longtext 
        Date - date
        Open - decimal 18, 4 
        High - decimal 18, 4 
        Low - decimal 18, 4 
        Close - decimal 18, 4 
        AdjClose - decimal 18, 4 
        Volume - bigint
    
Table 2

    table name: ReturnTable 
    
        ticker - char 6
        date - date
        return - decimal 18, 4
  
Table 3

    table name: RegressionTable ticker - char 6
    
        beta - decimal 18, 4
        alpha - decimal 18,4
        r2 - decimal 18, 4
        
## Portfolio Construction Strategy

Divided the cusips into two groups, whose betas are above and below target beta; In each group, chose five cusips with largest R-square as an equally weighted portfolio; Then, weighted between these two portfolios to get target beta, which can be calculated from a simple equation.

