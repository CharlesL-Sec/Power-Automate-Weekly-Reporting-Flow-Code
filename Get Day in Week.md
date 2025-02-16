# Get day in week by expression.



```javascript
addDays(utcNow('D'),
  if(equals(dayOfWeek(utcNow('D')),0),1,
    sub(8,dayOfWeek(utcNow('D')))
  )
)
```

### Explaination

- Get todays day
- if todays day is 0  and we which to return Monday 





```javascript
addDays(utcNow('D'),
  if(equals(dayOfWeek(utcNow('D')),0),1,
    sub(1,dayOfWeek(utcNow('D')))
  )
)

```
Returns **Monday**
