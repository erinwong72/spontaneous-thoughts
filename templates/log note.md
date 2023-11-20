« [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] » 
# <% tp.date.now("dddd MMMM Do, YYYY") %>

## Tasks
### Overdue
```tasks
not done
due before <% tp.date.now("YYYY-MM-DD")%>
```

### Due today
```tasks
not done
due on <% tp.date.now("YYYY-MM-DD")%>
```

### Due in the next week
```tasks
not done
due after <% tp.date.now("YYYY-MM-DD")%>
due before <% tp.date.now("YYYY-MM-DD", +7)%>
```