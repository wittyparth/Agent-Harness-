# 🗄️ DATABASE MASTERY

> **Complete knowledge for designing and operating production databases.**
> **What a 20+ year veteran engineer knows about data persistence.**

---

## 🎯 CORE MISSION

The database is the permanent memory of your application. Every other part can be rebuilt, but lost data is gone forever. Your job is to design systems that are:
- **Reliable**: Data is never lost or corrupted
- **Consistent**: Data integrity is maintained always
- **Performant**: Queries return quickly under load
- **Scalable**: Handles growth without redesign
- **Recoverable**: Can restore from any disaster

---

## 📋 COMPLETE DATABASE IMPLEMENTATION GUIDE

### PHASE 1: DATABASE SELECTION

#### 1.1 Relational (SQL) vs Non-Relational (NoSQL)

**Choose Relational (PostgreSQL, MySQL) When:**
- Data has clear relationships (users have orders, orders have items)
- You need ACID transactions (money transfers, inventory)
- Complex queries with joins, aggregations
- Data structure is known and stable
- Data integrity is critical

**Choose Document (MongoDB, DynamoDB) When:**
- Data structure varies significantly per record
- Hierarchical or nested data
- Rapid schema evolution needed
- Horizontal scaling is primary concern
- Simple access patterns (usually by ID)

**Choose Key-Value (Redis, Memcached) When:**
- Caching layer
- Session storage
- Rate limiting counters
- Simple get/set operations
- High speed is critical

**Choose Graph (Neo4j, Neptune) When:**
- Complex relationships are the main query
- Social networks, recommendation engines
- Fraud detection, knowledge graphs

**Default Recommendation**: PostgreSQL handles 95% of application needs. Start there unless you have a specific reason not to.

#### 1.2 Database Version Selection

- Use the latest stable version
- Check end-of-life dates (have a 5+ year runway)
- Verify cloud provider support if using managed service

---

### PHASE 2: SCHEMA DESIGN

#### 2.1 Normalization

**First Normal Form (1NF)**
- No repeating groups or arrays in columns
- Each column has atomic (indivisible) values

**Second Normal Form (2NF)**
- Must be in 1NF
- All non-key columns depend on the entire primary key

**Third Normal Form (3NF)**
- Must be in 2NF
- No transitive dependencies (non-key columns depending on other non-key columns)

**When to Denormalize:**
- Proven performance issues (not just anticipated)
- Read-heavy workloads where joins are expensive
- Aggregations/counts needed frequently
- Document WHY in a comment

#### 2.2 Table Design Standards

**Standard Columns Every Table Should Have:**
```
id            - Primary key (UUID for public-facing, serial for internal)
created_at    - When record was created (auto-set, never update)
updated_at    - When record was last modified (auto-update)
```

**Optional Standard Columns:**
```
deleted_at    - For soft deletes (NULL = not deleted)
created_by    - User who created (for audit)
updated_by    - User who last modified (for audit)
version       - For optimistic locking
```

#### 2.3 Naming Conventions

**Tables:**
- Plural, snake_case: `users`, `order_items`, `user_preferences`
- Descriptive, avoid abbreviations

**Columns:**
- Singular, snake_case: `user_id`, `created_at`, `is_active`
- Foreign keys match referenced table: `user_id` references `users.id`
- Boolean columns prefixed with `is_` or `has_`: `is_active`, `has_verified_email`
- Date columns suffixed with `_at` or `_on`: `created_at`, `expires_on`

**Indexes:**
- `idx_tablename_columnname` or `idx_tablename_col1_col2`

**Constraints:**
- Primary key: `pk_tablename`
- Foreign key: `fk_tablename_referenced`
- Unique: `uq_tablename_column`
- Check: `ck_tablename_column`

---

### PHASE 3: DATA TYPES

#### 3.1 Choosing the Right Type

| Data | Recommended Type | Avoid | Why |
|------|-----------------|-------|-----|
| **Primary key** | UUID or BIGINT | INT | INT exhausts at 2B rows |
| **Money** | DECIMAL(19,4) or cents INTEGER | FLOAT | Float has precision issues |
| **Text (bounded)** | VARCHAR(n) | CHAR or TEXT | CHAR wastes space, TEXT can be unbounded |
| **Text (unbounded)** | TEXT | VARCHAR(MAX) | TEXT is designed for it |
| **Boolean** | BOOLEAN | INT or CHAR(1) | Boolean is clearer |
| **Date only** | DATE | DATETIME | Date is more precise for intent |
| **Timestamp** | TIMESTAMPTZ | TIMESTAMP | Always store with timezone |
| **Email** | VARCHAR(255) | TEXT | Emails have a max length |
| **URL** | VARCHAR(2048) | TEXT | URLs have practical limits |
| **JSON** | JSONB (Postgres) | JSON or TEXT | JSONB is queryable, compressed |
| **IP Address** | INET (Postgres) | VARCHAR | Native type is more efficient |
| **Enum** | ENUM type or lookup table | VARCHAR | Enforces valid values |

#### 3.2 Nullability

**Column is NOT NULL when:**
- Value is always required
- Business logic doesn't allow absence
- It's a primary key or foreign key

**Column is NULL when:**
- Value might not exist
- Distinction between "empty" and "not set" matters
- Optional relationships

**Avoid NULL for:**
- Boolean columns (use default FALSE instead)
- Count/quantity columns (use default 0)
- String columns where empty string works

---

### PHASE 4: RELATIONSHIPS

#### 4.1 Relationship Types

**One-to-One**
- Rare in practice
- Use when: Splitting large table, optional data, different access patterns
- Implementation: Foreign key with UNIQUE constraint

**One-to-Many**
- Most common
- Example: User → Orders
- Implementation: Foreign key on the "many" side

**Many-to-Many**
- Requires junction table
- Example: Users ↔ Roles
- Implementation: Junction table with composite key

#### 4.2 Foreign Key Constraints

**Always define foreign keys**
- Prevents orphaned records
- Documents relationships
- Enables cascades

**ON DELETE options:**
| Option | When to Use |
|--------|-------------|
| CASCADE | Child is meaningless without parent (order_items when order deleted) |
| SET NULL | Child can exist without parent (posts when author deleted) |
| RESTRICT | Prevent deletion if children exist (users with active orders) |
| NO ACTION | Same as RESTRICT but checked at transaction end |

**ON UPDATE options:**
- Generally use CASCADE (when parent key changes)
- Better to use immutable primary keys

---

### PHASE 5: INDEXING

#### 5.1 When to Create Indexes

**Always Index:**
- Primary keys (automatic)
- Foreign keys (for JOIN performance)
- Columns in WHERE clauses used frequently
- Columns in ORDER BY clauses
- Columns with UNIQUE constraints

**Consider Indexing:**
- Columns in GROUP BY
- Columns used in JOIN conditions
- Low-cardinality columns with high selectivity in WHERE

**Avoid Indexing:**
- Tables with < 1000 rows (full scan is fine)
- Columns rarely used in queries
- Columns with very low cardinality (boolean, status)
- Wide columns (long strings)

#### 5.2 Index Types

| Type | Use Case |
|------|----------|
| **B-tree** | Default, good for equality and range queries |
| **Hash** | Equality only, faster for exact matches |
| **GIN** | Array, JSONB, full-text search |
| **GiST** | Geometric, range, full-text |
| **BRIN** | Very large tables with natural ordering |

#### 5.3 Composite Index Rules

**Column Order Matters**
- Put equality conditions first, range conditions last
- Index on (a, b) supports queries on (a) and (a, b), NOT (b) alone

**Covering Indexes**
- Include all columns needed for query
- Avoids table lookup (index-only scan)

#### 5.4 Index Maintenance

- Indexes slow down writes (INSERT, UPDATE, DELETE)
- Monitor index usage (unused indexes waste space/performance)
- Rebuild fragmented indexes periodically
- Analyze query plans to verify index usage

---

### PHASE 6: QUERY OPTIMIZATION

#### 6.1 Query Analysis

**Use EXPLAIN ANALYZE**
- Shows actual execution plan
- Reveals where time is spent
- Shows row estimates vs actuals

**Warning Signs:**
- Sequential scans on large tables
- Nested loops with many iterations
- Hash/sort operations spilling to disk
- Large discrepancy between estimated and actual rows

#### 6.2 Common Optimization Techniques

**Avoid SELECT ***
- Specify only needed columns
- Reduces I/O and memory
- Allows covering indexes

**Avoid N+1 Queries**
- Don't query in loops
- Use JOINs or batch queries
- Use eager loading in ORMs

**Pagination Optimization**
- Offset/limit is slow for deep pages
- Use keyset/cursor pagination: `WHERE id > last_seen_id LIMIT n`

**Avoid Functions on Indexed Columns**
- `WHERE YEAR(created_at) = 2024` can't use index
- Rewrite as: `WHERE created_at >= '2024-01-01' AND created_at < '2025-01-01'`

**Use EXISTS Instead of COUNT for Existence Checks**
- `IF EXISTS (SELECT 1 FROM orders WHERE user_id = ?)` stops at first match
- `IF (SELECT COUNT(*) FROM orders WHERE user_id = ?) > 0` scans all

---

### PHASE 7: TRANSACTIONS

#### 7.1 ACID Properties

| Property | Meaning |
|----------|---------|
| **Atomicity** | All or nothing - transaction fully completes or fully rolls back |
| **Consistency** | Database always moves from valid state to valid state |
| **Isolation** | Concurrent transactions don't interfere |
| **Durability** | Committed transactions survive crashes |

#### 7.2 When to Use Transactions

**Always Use Transactions For:**
- Multiple related writes (all succeed or none)
- Money/inventory operations
- Maintaining referential integrity
- Complex business operations

**Transaction Boundaries:**
- Keep transactions as short as possible
- Avoid long-running transactions (block other operations)
- Avoid user interaction within transaction

#### 7.3 Isolation Levels

| Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|-------|------------|---------------------|--------------|
| Read Uncommitted | Yes | Yes | Yes |
| Read Committed | No | Yes | Yes |
| Repeatable Read | No | No | Yes |
| Serializable | No | No | No |

**Default**: Read Committed (good balance)
**Use Serializable**: For critical sections where consistency is paramount

#### 7.4 Optimistic vs Pessimistic Locking

**Optimistic Locking**
- Add version column
- Check version on update: `WHERE id = ? AND version = ?`
- If no rows updated, conflict occurred
- Use when: Conflicts are rare

**Pessimistic Locking**
- Lock row on read: `SELECT ... FOR UPDATE`
- Other transactions wait
- Use when: Conflicts are common, operation is quick

---

### PHASE 8: MIGRATIONS

#### 8.1 Migration Principles

**Every Schema Change is a Migration**
- Never manually alter production database
- Migrations are version controlled
- Migrations are reversible (up and down)
- Test migrations before production

**Migration Naming**
- Include timestamp: `20240115_120000_create_users_table`
- Descriptive: `add_email_verified_at_to_users`

#### 8.2 Safe Migration Practices

**Adding Columns**
- Safe: Add with NULL allowed or with DEFAULT
- Risk: Adding NOT NULL to existing table requires backfill

**Removing Columns**
- Step 1: Remove all code references
- Step 2: Deploy code changes
- Step 3: Drop column in next migration
- Never drop and deploy together

**Renaming Columns**
- Never rename directly (breaks running code)
- Step 1: Add new column
- Step 2: Backfill data
- Step 3: Update code to use new column
- Step 4: Drop old column

**Adding Indexes on Large Tables**
- Use CONCURRENTLY (in Postgres) to avoid locking
- Schedule during low-traffic periods

---

### PHASE 9: BACKUP & RECOVERY

#### 9.1 Backup Types

| Type | What It Captures | Recovery Speed |
|------|------------------|---------------|
| **Full Backup** | Entire database | Slowest |
| **Incremental** | Changes since last backup | Medium |
| **Point-in-Time** | Continuous (WAL/binlog) | Fast, any point |

#### 9.2 Backup Strategy

**3-2-1 Rule**
- 3 copies of data
- 2 different storage types
- 1 off-site (different geographic location)

**Backup Schedule**
- Full: Daily
- Incremental: Hourly
- Point-in-time: Continuous

#### 9.3 Recovery Testing

**Test Restores Regularly (Monthly)**
- Verify backups are complete
- Measure recovery time
- Practice the procedure
- Document exact steps

**Define RTO and RPO**
- Recovery Time Objective (RTO): How long until restored?
- Recovery Point Objective (RPO): How much data can be lost?
- Design backup strategy to meet these

---

### PHASE 10: CONNECTION MANAGEMENT

#### 10.1 Connection Pooling

**Why Pool:**
- Connection creation is expensive (TCP, auth, etc.)
- Database has max connection limit
- Pooling reuses connections

**Pool Sizing Formula:**
```
Optimal size ≈ (2 × CPU cores) + number of disk drives
```

For web apps: Start with 10-20, adjust based on monitoring

**Pool Configuration:**
- Min connections: Keep some ready (5-10)
- Max connections: Hard limit (matches DB limit / instances)
- Idle timeout: Return idle connections (30-60 seconds)
- Max lifetime: Replace old connections (30-60 minutes)

#### 10.2 Connection Best Practices

- Return connections promptly (don't hold during HTTP request)
- Don't create connections in loops
- Configure timeout (don't wait forever for connection)
- Monitor pool utilization

---

### PHASE 11: SECURITY

#### 11.1 Access Control

**Principle of Least Privilege**
- Application user has only needed permissions
- No DROP, CREATE, GRANT in production app user
- Separate read-only user for reporting

#### 11.2 Data Protection

**Encryption at Rest**
- Enable database-level encryption
- Encrypt highly sensitive columns (SSN, tokens)

**Encryption in Transit**
- Require TLS for database connections
- No plain-text connections

**Credential Management**
- Different passwords per environment
- Rotate passwords regularly
- Use managed credentials where possible

#### 11.3 Preventing Injection

**Always Use Parameterized Queries**
- Never concatenate user input into SQL
- Use ORM/query builder
- Treat all input as untrusted

---

## ✅ DATABASE QUALITY CHECKLIST

Before marking database complete:

### Schema
- [ ] Tables follow naming conventions
- [ ] Proper data types used
- [ ] Standard columns present (id, created_at, updated_at)
- [ ] Foreign keys defined with appropriate actions
- [ ] Normalization appropriate (3NF or documented exception)
- [ ] Constraints in place (NOT NULL, UNIQUE, CHECK)

### Performance
- [ ] Indexes on all foreign keys
- [ ] Indexes on frequently queried columns
- [ ] No N+1 queries
- [ ] Query plans analyzed for critical paths
- [ ] Connection pooling configured

### Operations
- [ ] Migrations versioned and reversible
- [ ] Backup strategy in place
- [ ] Recovery tested
- [ ] Monitoring configured
- [ ] Slow query logging enabled

### Security
- [ ] Application user has minimal privileges
- [ ] Encryption at rest enabled
- [ ] TLS required for connections
- [ ] Credentials stored securely
- [ ] All queries parameterized

---

## 💡 HARD-LEARNED LESSONS

1. **Schema design is hard to change later**: Get it right up front, normalize properly.

2. **Indexes are not free**: They speed reads but slow writes. Measure, don't guess.

3. **Backup verification is as important as backups**: Untested backups are Schrödinger's backups.

4. **The database is usually the bottleneck**: Profile queries before optimizing code.

5. **Connection pools save you**: Running out of connections crashes your app.

6. **Null is not zero, empty string, or false**: Treat NULL correctly or bugs will haunt you.

7. **Data migrations are code too**: Version them, test them, review them.

8. **Soft deletes have trade-offs**: They complicate queries and accumulate data.

9. **ORMs abstract but don't eliminate**: You still need to understand SQL.

10. **Data outlives code**: Systems get rewritten, database designs persist.

---

**Apply this knowledge to every database decision.**
