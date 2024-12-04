# JSTL Core Library Comprehensive Guide

## 📘 Overview
The JSTL Core Library provides fundamental tags for basic programming tasks in JSP, simplifying common operations like variable manipulation, conditional logic, and iteration.

## 🏷️ Core Library Tags Reference

### 1. Variable Manipulation

#### `<c:set>` - Variable Assignment
**Description:** Creates a variable or updates an existing variable in a specified scope.

```jsp
<%-- Set a simple variable --%>
<c:set var="username" value="JohnDoe" />

<%-- Set a variable in a specific scope --%>
<c:set var="userCount" value="100" scope="session" />

<%-- Set a variable from an object property --%>
<c:set var="userEmail" value="${user.email}" />
```

#### `<c:remove>` - Variable Removal
**Description:** Removes a variable from a specified scope.

```jsp
<%-- Remove a variable from request scope --%>
<c:remove var="tempUser" scope="request" />
```

### 2. Conditional Logic

#### `<c:if>` - Simple Conditional
**Description:** Renders content only if the test condition is true.

```jsp
<c:if test="${user.age >= 18}">
    <p>Welcome, Adult User!</p>
</c:if>
```

#### `<c:choose>` - Complex Conditional
**Description:** Provides multi-condition branching similar to switch statements.

```jsp
<c:choose>
    <c:when test="${user.score >= 90}">
        Excellent Performance
    </c:when>
    <c:when test="${user.score >= 70}">
        Good Performance
    </c:when>
    <c:otherwise>
        Needs Improvement
    </c:otherwise>
</c:choose>
```

### 3. Iteration

#### `<c:forEach>` - Collection Iteration
**Description:** Iterates over collections, arrays, or a range of values.

```jsp
<%-- Iterate over a collection --%>
<c:forEach items="${users}" var="user" varStatus="status">
    ${status.index + 1}: ${user.name}
</c:forEach>

<%-- Iterate over a range --%>
<c:forEach begin="1" end="5" var="number">
    Number: ${number}
</c:forEach>
```

#### `<c:forTokens>` - String Tokenization
**Description:** Splits a string and iterates over its tokens.

```jsp
<c:forTokens items="Java,Python,JavaScript" delims="," var="language">
    Programming Language: ${language}
</c:forTokens>
```

### 4. URL Handling

#### `<c:url>` - URL Construction
**Description:** Generates a URL with optional parameters, handling context path and encoding.

```jsp
<%-- Simple URL --%>
<c:url value="/profile" var="profileUrl" />

<%-- URL with Parameters --%>
<c:url value="/search" var="searchUrl">
    <c:param name="query" value="${searchTerm}" />
    <c:param name="category" value="books" />
</c:url>
```

### 5. Output and Escaping

#### `<c:out>` - Safe Output
**Description:** Displays content with optional default and XML escaping.

```jsp
<%-- Basic output --%>
<c:out value="${userInput}" />

<%-- With default value --%>
<c:out value="${potentiallyNullValue}" default="N/A" />

<%-- Escape XML content --%>
<c:out value="${userInput}" escapeXml="true" />
```

### 6. Flow Control

#### `<c:import>` - Content Inclusion
**Description:** Includes content from another resource, like a URL or local file.

```jsp
<%-- Import from a relative path --%>
<c:import url="header.jsp" />

<%-- Import from an external URL --%>
<c:import url="https://example.com/banner.html" />
```

#### `<c:redirect>` - Page Redirection
**Description:** Redirects to another page with optional parameters.

```jsp
<%-- Simple Redirect --%>
<c:redirect url="/login" />

<%-- Redirect with Parameters --%>
<c:redirect url="/dashboard">
    <c:param name="message" value="Login Successful" />
</c:redirect>
```

## 📋 Quick Reference

| Tag | Primary Purpose | Key Attributes |
|-----|----------------|----------------|
| `<c:set>` | Variable Assignment | `var`, `value`, `scope` |
| `<c:remove>` | Variable Removal | `var`, `scope` |
| `<c:if>` | Conditional Rendering | `test` |
| `<c:choose>` | Multi-Condition Branching | N/A (uses `<c:when>`, `<c:otherwise>`) |
| `<c:forEach>` | Iteration | `items`, `var`, `begin`, `end` |
| `<c:url>` | URL Construction | `value`, `var` |
| `<c:out>` | Safe Output | `value`, `default`, `escapeXml` |

## 🔑 Key Considerations
- Always use `escapeXml="true"` to prevent XSS vulnerabilities
- Prefer JSTL over scriptlets for cleaner, more maintainable code
- Use scope attributes judiciously to manage variable lifecycle
