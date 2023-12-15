# Stock-Portfolio-Project
I wanted to create an online Stock Portfolio that is dynamic to the changes appearing in the stock market daily
# Dynamic Stock Portfolio:

* I therefore decided to use google sheets to make it dynamic as possible.
* I used the following formulas:

### Positions Tab:
* 🔸MyPortfolio: =MyPortfolio(History!B3:B1001,History!D3:D1001)    
* Purchase:=if(isblank(A3),"",AVERAGE.WEIGHTED(FILTER(History!E:E,History!B:B=A3,History!D:D▶0),FILTER(History!D:D,History!B:B=A3,History!D:D▶0)))
* 🔸Price: =if(ISBLANK(A3),"",GOOGLEFINANCE(A3,"Price"))
* 🔸Change%: =if(ISBLANK(A3),"",GOOGLEFINANCE(A3,"changepct")/100)
* 🔸Change$: =if(ISBLANK(A3),"",GOOGLEFINANCE(A3,"change")*B3)
* 🔸Cost: =if(ISBLANK(A3),"",C3*B3)
* 🔸Value: =if(ISBLANK(A3),"",D3*B3)
* 🔸Gain%: =if(isblank(A3),"",(D3-C3)/C3)
* 🔸Gain$: =if(ISBLANK(A3),"",H3-G3)
      
### Dashboard Tab:
* 🔸 Account Value: =B3+B4
* 🔸 Positions: =SUM(Positions!H3:H30)
* 🔸 Cash: =sumif(History!C:C,"Deposit",History!F:F)-sumif(History!C:C,"Withdrawal",History!F:F)+sumif(History!C:C,"Sell",History!F:F)-sumif(History!C:C,"Buy",History!F:F)

* 🔸 Day change: =sum(Positions!F3:F30)
* 🔸 Unrealized Gains: =sum(Positions!J3:J30)
* 🔸 Realized Gains: =sumif(History!C:C,"Sell",History!F:F)-sumif(History!C:C,"Buy",History!F:F)-sumif(History!C:C,"DRIP",History!F:F)+sum(Positions!G3:G30)

* 🔸 Number of Trades: =countif(History!C:C,"Buy")+countif(History!C:C,"Sell")
* 🔸 Shares Owned: =sum(Positions!B3:B20)
* 🔸 Average Share Cost: =(Sum(Positions!G3:G16))/B10
* 🔸 Number of cash deposits: =countif(History!C:C,"Deposit")
* 🔸 Money Hourly Salary: =(B6+B7)/2080
* 🔸 Dividend Income: =sumif(History!C:C,"DRIP",History!F:F)

#### I also used the following code using script editor:

``` function myPortfolio(tickers,values) {
   var total = []
   var sums = {}

   for(i=0;i<tickers.length;i++){

    var t = tickers[i].toString()

    if(t !="Cash"){

      if(t in sums){
        sums[t]+= Number(values[i])
      }
      else{
        sums[t] = Number(values[i])
      }
    }
   }
   for(var ticker in sums){
      if(sums[ticker]>0){
        total.push([ticker.sums[ticker]])
      }
   }
   return total
}
```

The link is here of the original file https://docs.google.com/spreadsheets/d/1KUI7x8sMYRl4bnAgojX6avk4fiUIWjTHgVWrQxNh-ik/edit#gid=0
Also for the code https://script.google.com/u/0/home/projects/1qNJvnnKzKNj9auzyfn8pHUM1GslChBvXLOThJ75wu5M_6jTdYeRmahzZ/edit
