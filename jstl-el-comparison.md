# JSTL Core Library and Expression Language (EL) Comparison

## 📌 Variable Manipulation

### JSTL
```jsp
<%-- Set a variable --%>
<c:set var="username" value="JohnDoe" scope="request" />

<%-- Remove a variable --%>
<c:remove var="username" scope="request" />
```

### Expression Language (EL)
```jsp
<%-- Direct variable access --%>
${username}

<%-- Scope-specific access --%>
${requestScope.username}
```

## 🔀 Conditional Statements

### JSTL
```jsp
<%-- Simple If --%>
<c:if test="${age >= 18}">
    You are an adult
</c:if>

<%-- Choose/When/Otherwise --%>
<c:choose>
    <c:when test="${score >= 90}">
        Excellent
    </c:when>
    <c:when test="${score >= 70}">
        Good
    </c:when>
    <c:otherwise>
        Needs Improvement
    </c:otherwise>
</c:choose>
```

### Expression Language (EL)
```jsp
<%-- Ternary Conditional --%>
${age >= 18 ? 'Adult' : 'Minor'}

<%-- Null/Empty Check --%>
${empty username ? 'Guest' : username}
```

## 🔁 Iteration

### JSTL
```jsp
<%-- Iterate over Collection --%>
<c:forEach items="${users}" var="user" varStatus="status">
    ${status.index}: ${user.name}
</c:forEach>

<%-- Range Iteration --%>
<c:forEach begin="1" end="5" var="num">
    Number: ${num}
</c:forEach>
```

### Expression Language (EL)
```jsp
<%-- Collection Size --%>
Total Users: ${users.size()}

<%-- Accessing Collection Elements --%>
First User: ${users[0].name}
```

## 🧮 Arithmetic and Logical Operations

### JSTL
```jsp
<%-- Arithmetic --%>
<c:set var="total" value="${price * quantity}" />

<%-- Logical Operations --%>
<c:if test="${isAdmin and canEdit}">
    Edit Allowed
</c:if>
```

### Expression Language (EL)
```jsp
<%-- Direct Arithmetic --%>
Total: ${price * quantity}

<%-- Logical Expressions --%>
${isAdmin && canEdit ? 'Can Edit' : 'No Permission'}
```

## 🔗 URL Handling

### JSTL
```jsp
<%-- URL with Parameters --%>
<c:url value="/profile" var="profileUrl">
    <c:param name="userId" value="${user.id}" />
</c:url>

<a href="${profileUrl}">View Profile</a>
```

### Expression Language (EL)
```jsp
<%-- URL Construction --%>
<a href="/profile?userId=${user.id}">View Profile</a>
```

## 🎯 Comparison Operators

### JSTL
```jsp
<c:if test="${salary eq 50000}">
    Standard Salary
</c:if>

<c:if test="${age gt 18 and age lt 65}">
    Working Age Group
</c:if>
```

### Expression Language (EL)
```jsp
<%-- Comparison Operators --%>
${salary == 50000 ? 'Standard' : 'Variable'}

${age > 18 && age < 65 ? 'Working Age' : 'Other'}
```

## 📝 Error Handling and Output

### JSTL
```jsp
<%-- Safe Output --%>
<c:out value="${userInput}" escapeXml="true" default="N/A" />
```

### Expression Language (EL)
```jsp
<%-- Null Coalescing --%>
${userInput == null ? 'N/A' : userInput}
```

## 📋 Key Differences

| Aspect | JSTL | Expression Language (EL) |
|--------|------|--------------------------|
| Syntax | Tag-based | `${}` expression-based |
| Complexity | More verbose | More concise |
| Use Case | Complex logic | Simple value expressions |
