« [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] » 
# <% tp.date.now("dddd MMMM Do, YYYY") %>

## Tasks
>[!check]- New task
### Overdue
```tasks
hide backlink
not done
(due before <% tp.date.now("YYYY-MM-DD")%>) OR (scheduled before <% tp.date.now("YYYY-MM-DD")%>)
```

### Due today
```tasks
hide backlink
not done
(due on <% tp.date.now("YYYY-MM-DD")%>) OR (scheduled on <% tp.date.now("YYYY-MM-DD")%>)
```

### Due in the next week
```tasks
hide backlink
not done
(due after <% tp.date.now("YYYY-MM-DD")%>) OR (scheduled after <% tp.date.now("YYYY-MM-DD")%>)
(due before <% tp.date.now("YYYY-MM-DD", +7)%>) OR (scheduled before <% tp.date.now("YYYY-MM-DD", +7)%>)
```