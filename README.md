# Code review issues

### ShoppingCart class:
- #### Problem:
  ```productQuantities``` Map updates:  
  This method updates the ```productQuantities``` map by checking if the product is already in the map. 
  However, this approach calls ```productQuantities.get(product)``` twice: once in the containsKey check and once when updating the value. 
  This is inefficient. 
- #### Problem:
  Multiple ```if``` Statements:  
  There are several ```if``` statements checking the value of ```offer.offerType``` for different offer types (e.g., ```SpecialOfferType.THREE_FOR_TWO```, ```SpecialOfferType.TWO_FOR_AMOUNT```, etc.).
  It can cause difficulty in extending the code: If new offer types are added in the future, there is need to add more else if blocks. This can make the code harder to maintain and extend over time.
  What is more, there is potential for logical errors: With multiple ```if-else``` conditions, it's easy to miss a condition or introduce overlapping logic, leading to difficult to diagnose bugs.
- #### Problem:
  Poor naming conventions:  
  The variable names, such as ```x``` and ```discountN```, could be more descriptive.
- #### Problem:
  Magic numbers:  
  In the ```handleOffers``` method, ```x = 3;```, ```x = 2;```, and other similar values are hard-coded ("magic numbers").
- #### Problem:
  Potential NullPointerException:  
  In line 37: ```double quantity = productQuantities.get(p);``` if ```productQuantities``` does not contain the key p, it will return ```null``` and lead to a ```NullPointerException```. 