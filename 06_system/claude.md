## Optimization Strategies

*Strategies to reduce token spending and improve caching efficiency:*  

1. **Limit Context Reloads:**  
   Load only necessary context to avoid excess token consumption.  

2. **Batch Requests:**  
   Combine similar requests into one to minimize overhead.  

3. **Shorten Confirmations:**  
   Use concise confirmations and output; stick to essential information.  

4. **Monitor Cache Hit Rates:**  
   Aim for above 90% to maximize context reuse efficiency.  

5. **Set Performance Targets:**  
   Define metrics for token use and implement regular checks to maintain efficiency.  

6. **Use Efficient Models:**  
   Retain Haiku for regular tasks and utilize Sonnet only for complex requests.  

7. **Throttle Redundant Commands:**  
   Avoid re-checking systems in unnecessary loops to keep token costs down.
