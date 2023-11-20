« [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] » 
# <% tp.date.now("dddd MMMM Do, YYYY") %>

## Tasks
### Overdue
```tasks
not done
due before {{date:YYYY-MM-DD}}
```

### Due today
```tasks
not done
due on {{date:YYYY-MM-DD}}
```

### Due in the next week
```tasks
not done
due after {{date:YYYY-MM-DD}}
due before {{date+7d:YYYY-MM-DD}}
```

### No due date
```tasks
not done
no due date
```