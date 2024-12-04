# JSP Expression Comparison: Scriptlet vs JSTL vs Expression Language

## Overview

JSP (JavaServer Pages) provides multiple ways to embed dynamic content. This guide compares three primary methods:
- Scriptlets
- JSTL (JavaServer Pages Standard Tag Library)
- Expression Language (EL)

## Comparison Matrix

| Feature | Scriptlet `<% %>` | JSTL | Expression Language `${}` |
|---------|-------------------|------|---------------------------|
| **Syntax** | Java code | XML-like tags | `${expression}` |
| **Readability** | Low | Medium | High |
| **Separation of Concerns** | Poor | Good | Excellent |
| **Performance** | Slowest | Moderate | Fastest |
| **Type Safety** | Full Java typing | Limited | Automatic type coercion |

## 1. Variable Declaration

### Scriptlet
```jsp
<% 
    String name = "John Doe"; 
    int age = 30; 
%>
```

### JSTL
```jsp
<c:set var="name" value="John Doe" />
<c:set var="age" value="30" />
```

### Expression Language
```jsp
<%-- EL is for reading, not direct assignment --%>
${name}  <%-- Reads the value --%>
```

## 2. Conditional Logic

### Scriptlet
```jsp
<% 
    if (user != null && user.getAge() >= 18) { 
%>
    Adult User
<% 
    } else { 
%>
    Minor User
<% 
    } 
%>
```

### JSTL
```jsp
<c:if test="${user.age >= 18}">
    Adult User
</c:if>
<c:choose>
    <c:when test="${user.age >= 18}">Adult User</c:when>
    <c:otherwise>Minor User</c:otherwise>
</c:choose>
```

### Expression Language
```jsp
${user.age >= 18 ? 'Adult User' : 'Minor User'}
```

## 3. Iteration

### Scriptlet
```jsp
<% 
    List<String> users = (List<String>)request.getAttribute("users");
    for (String user : users) { 
%>
    <%= user %>
<% 
    } 
%>
```

### JSTL
```jsp
<c:forEach items="${users}" var="user">
    ${user}
</c:forEach>
```

### Expression Language
```jsp
${users[0]}  <%-- First user --%>
${users.size}  <%-- Collection size --%>
```

## 4. Output Handling

### Scriptlet
```jsp
<%= request.getAttribute("username") %>
```

### JSTL
```jsp
<c:out value="${username}" default="Guest" escapeXml="true" />
```

### Expression Language
```jsp
${empty username ? 'Guest' : username}
```

## Best Practices

1. **Avoid Scriptlets**: They mix presentation and logic
2. **Prefer Expression Language**: For simple value expressions
3. **Use JSTL**: For complex logic and control flow
4. **Always Escape Output**: Prevent XSS vulnerabilities

## Compatibility Notes

- EL supported in JSP 2.0+
- JSTL requires additional tag library imports
- Scriptlets are legacy but still supported

## Recommendation Hierarchy

1. Expression Language `${}` 
2. JSTL Tags `<c:xxx>`
3. Scriptlets `<% %>` (Avoid if possible)

## Required Imports

### JSTL Core Library
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

### Expression Language
- Typically built-in with modern Java EE containers
- No explicit import usually required

## Practical Tips

- Use EL for simple value display
- Use JSTL for control flow and complex logic
- Keep Java code in servlets/controllers
- Minimize logic in view layers
