# 📜 VALIDATION CONTRACTS

> **Shared validation rules between frontend and backend.**
> **Both sides MUST implement these exact rules.**

---

## ⚠️ IMPORTANT

Validation rules defined here must be implemented identically on:
- Frontend (for UX)
- Backend (for security)

**Never trust frontend validation alone. Backend is the source of truth.**

---

## 📋 Validation Rules Template

### User Fields

| Field | Type | Required | Rules |
|-------|------|----------|-------|
| email | string | Yes | Valid email format, max 255 chars, lowercase |
| password | string | Yes | Min 8 chars, max 128 chars |
| name | string | Yes | Min 1 char, max 100 chars, trimmed |
| avatarUrl | string | No | Valid URL, max 2048 chars, HTTPS only |

### Email Validation
```
- Required
- Valid email format (regex or library)
- Maximum 255 characters
- Normalize to lowercase
- Trim whitespace
- No leading/trailing spaces
```

### Password Validation
```
- Required
- Minimum 8 characters
- Maximum 128 characters
- No leading/trailing whitespace
- (Optional) Require: uppercase, lowercase, number, special char
- (Recommended) Check against breached password list
```

### Name Validation
```
- Required
- Minimum 1 character
- Maximum 100 characters
- Trim whitespace
- No control characters
```

---

## 📋 Common Field Types

### ID Fields
```
- UUID v4 format
- Valid: 550e8400-e29b-41d4-a716-446655440000
- Regex: ^[0-9a-f]{8}-[0-9a-f]{4}-4[0-9a-f]{3}-[89ab][0-9a-f]{3}-[0-9a-f]{12}$
```

### Date Fields
```
- ISO 8601 format
- Valid: 2024-01-15T10:30:00.000Z
- Timezone: UTC (Z suffix)
```

### URL Fields
```
- Valid URL format
- Maximum 2048 characters
- Must be HTTPS in production
```

### Pagination
```
page:
  - Integer
  - Minimum: 1
  - Default: 1

limit:
  - Integer
  - Minimum: 1
  - Maximum: 100
  - Default: 20

sortOrder:
  - Enum: 'asc' | 'desc'
  - Default: 'desc'
```

---

## 📋 Resource Validation Template

```yaml
# Create Resource Request
CreateResourceRequest:
  name:
    type: string
    required: true
    minLength: 1
    maxLength: 100
    transform: trim
    
  description:
    type: string
    required: false
    maxLength: 1000
    transform: trim
    default: null
    
  status:
    type: enum
    required: false
    values: [draft, active, archived]
    default: draft
    
# Update Resource Request (all fields optional)
UpdateResourceRequest:
  name:
    type: string
    required: false
    minLength: 1
    maxLength: 100
    transform: trim
    
  description:
    type: string
    required: false
    maxLength: 1000
    transform: trim
    nullable: true    # Can set to null to clear
    
  status:
    type: enum
    required: false
    values: [draft, active, archived]
```

---

## 📋 Error Response Format

All validation errors return 400 with this format:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      },
      {
        "field": "password",
        "message": "Password must be at least 8 characters"
      }
    ]
  }
}
```

---

## 📋 Validation Error Messages

Use these consistent error messages:

| Rule | Message |
|------|---------|
| Required | "{field} is required" |
| Min length | "{field} must be at least {min} characters" |
| Max length | "{field} must be at most {max} characters" |
| Email format | "Invalid email format" |
| URL format | "Invalid URL format" |
| UUID format | "Invalid ID format" |
| Enum | "{field} must be one of: {values}" |
| Min number | "{field} must be at least {min}" |
| Max number | "{field} must be at most {max}" |
| Pattern | "{field} format is invalid" |

---

## 📋 Adding New Validations

When adding validation for a new field:

1. Document the rules in this file
2. Implement on backend
3. Implement on frontend
4. Add validation tests
5. Update API contract error responses
6. Update error message documentation

---

## 📋 Validation Libraries

Recommended approach: Use the same validation schema on both sides.

```yaml
# Define once in this file
# Implement with:
# - Backend: Zod, Joi, Yup, or framework validator
# - Frontend: Same library (Zod works well for both)
```

---

**Keep frontend and backend validation in sync.**
