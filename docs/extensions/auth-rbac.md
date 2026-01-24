# FORGE Auth & RBAC

**Identity and permission foundation for FORGE projects.**

**Version:** 1.1
**Status:** Extension (Required for Software Projects)
**Added:** 2026-01-23

---

## What Auth/RBAC Is

Auth/RBAC provides the **identity and permission foundation** for FORGE software projects. It establishes:

1. **User Identity** — Who is this person? (authentication)
2. **Organization Context** — Which tenant are they operating in? (tenancy)
3. **Role-Based Access** — What are they allowed to do? (authorization)

**Auth/RBAC is not optional for software projects.** Every FORGE software project ships with authentication and role-based access control from Day One. Stakeholders log in before MVP code exists.

---

## What Auth/RBAC Is NOT

| Auth/RBAC Does NOT | Why |
|--------------------|-----|
| Prescribe specific auth providers | Projects choose their stack (Supabase, Auth0, etc.) |
| Define application-specific permissions | RBAC provides foundation; apps add granularity |
| Require SSO from Day One | Email auth is sufficient for launch |
| Replace application logic | Auth gates access; business logic decides outcomes |

---

## Platform vs Tenant Planes

FORGE SaaS projects operate on two distinct planes:

### Platform Plane

| Attribute | Description |
|-----------|-------------|
| **Scope** | System-wide; not scoped to any organization |
| **Actors** | Stakeholders, platform administrators |
| **Surfaces** | Stakeholder Portal, Stakeholder AI |
| **Access** | Invite-only |

The platform plane is **supra-tenant**. It provides visibility into the SaaS platform itself (roadmap, execution, feedback) without exposing tenant data.

### Tenant Plane

| Attribute | Description |
|-----------|-------------|
| **Scope** | Scoped to a specific organization (tenant) |
| **Actors** | Owners, Admins, Members |
| **Surfaces** | Tenant application, business workflows |
| **Access** | Per organizational membership |

The tenant plane is where business operations occur, scoped to specific organizations.

### Session Invariant

**A session is always scoped to exactly one plane.**

- Platform session → Stakeholder Portal only
- Tenant session → Tenant application for that org only

No cross-visibility. No implicit access. Switching planes requires logout/login or equivalent hard context reset.

---

## The Org-Centric Identity Model (Tenant Plane)

Within the tenant plane, FORGE uses an **organization-centric identity model**. Users exist globally; tenant roles exist within organizations.

```
User (global identity)
├── email, name, profile
└── belongs to → Memberships (many)
                 ├── Organization A → roles: [owner, member]
                 └── Organization B → roles: [admin]
```

**Note:** Stakeholder access is handled separately via platform memberships. See [Platform Memberships](#platform-memberships).

### Key Principle

**Roles are scoped to memberships, not users.**

A user may be an Owner in one organization and a Stakeholder in another. The role attaches to the relationship, not the person.

### What Counts as an "Organization"

Organizations are tenant boundaries. In FORGE projects, organizations may represent:

- Ventures or startups
- Clients or customers
- Cohorts or groups
- Partners or vendors
- Any logical boundary that scopes data and permissions

---

## The Three Tenant Roles

FORGE defines three standard **tenant-level roles**. These roles exist within organizations (tenants) and are **additive capability grants**, not exclusive modes.

| Role | Description | Typical Capabilities |
|------|-------------|---------------------|
| **Owner** | Ultimate authority over the organization | All capabilities + org management + ownership transfer |
| **Admin** | Manages users and settings | User management, role assignment, configuration |
| **Member** | Standard team participant | Create/edit resources, collaborate, view org content |

**Note:** Stakeholder is a **platform-level actor**, not a tenant role. See [Platform Memberships](#platform-memberships).

### Multi-Role Users (Within Tenant Plane)

Users may hold multiple **tenant roles** simultaneously within an organization. Examples:

| Pattern | Roles | Use Case |
|---------|-------|----------|
| Founder | Owner + Admin | Full authority with administrative access |
| Team Lead | Admin + Member | Manages team while also contributing |

**No role-switching UX within a plane.** Surfaces unlock based on role presence.

**Dual-Plane Humans:** A single human may operate in both planes (platform and tenant), but must use **separate identities**. See [Dual-Plane Human Identity Pattern](#dual-plane-human-identity-pattern).

### Role Hierarchy (Tenant Plane)

Tenant roles follow a capability hierarchy:

```
Owner
  └─▶ Admin
        └─▶ Member
```

Higher roles inherit lower role capabilities. An Owner can do anything an Admin can do.

**Note:** Stakeholder is not in this hierarchy. Stakeholders operate in the platform plane, not the tenant plane.

---

## Platform Memberships

FORGE distinguishes **platform memberships** from **tenant memberships**.

### Platform Memberships (Supra-Tenant)

Platform memberships grant access to the platform plane:

```
platform_memberships
├── email (stakeholder email)
├── invited_by (platform admin)
├── status (pending | active | revoked)
└── role (stakeholder)
```

**Characteristics:**
- Invite-only (no public signup)
- Not scoped to any tenant
- Separate from tenant memberships
- Used for Stakeholder Portal access

### Tenant Memberships (Within Organizations)

Tenant memberships grant access to specific organizations:

```
memberships
├── user_id
├── org_id
└── roles[] (owner, admin, member)
```

These are independent systems with no foreign key relationship.

### Stakeholder as Platform Actor

**Stakeholders are the first live users of any FORGE project.**

Before MVP code exists, stakeholders log in to the Stakeholder Interface. This exercises auth immediately and establishes the feedback loop.

Stakeholder is NOT:
- A tenant-level role
- A boolean flag on users
- Scoped to any organization

Stakeholder IS:
- A platform-level actor
- Managed via platform memberships
- The entry point for product visibility and feedback

---

## Dual-Plane Human Identity Pattern

A single human may operate in both planes. When they do:

| Requirement | Description |
|-------------|-------------|
| **Separate identities** | Different email address per plane |
| **Separate credentials** | Different password, MFA |
| **Separate sessions** | Cannot be in both planes simultaneously |
| **No automatic linkage** | System does not associate identities |

**Example:**
- Stakeholder identity: `alice@stakeholder.example.com`
- Tenant identity: `alice@tenant.example.com`

This is the FORGE default. Clarity and audit trail integrity take precedence over convenience.

**Switching planes requires logout/login.** There is no in-session plane switching in Phase 0.

---

## Two-Phase Authentication (Tenant Plane)

For tenant plane access, FORGE auth operates in two phases:

### Phase 1: Identity

Verify who the user is:
- Email/password
- SSO (future)
- Magic link (optional)

Output: Authenticated session with user identity.

### Phase 2: Context

Establish organizational context:
- If user has one org: auto-select
- If user has multiple orgs: user selects
- Load roles for selected org

Output: Scoped session with org context and roles.

This separation enables:
- Multi-org users without confusion
- Clear permission boundaries per org
- Future: org-switching without re-auth

---

## Permission Enforcement

### The Principle

**Enforce at the data layer, not the application layer.**

Application code may have bugs. The data layer (RLS, policies) is the last line of defense.

### Enforcement Pattern

```
Request arrives
    ↓
Application checks role (UX gating)
    ↓
Database enforces tenant isolation (security)
    ↓
Data returned (only what user can see)
```

Even if application code fails to check permissions, the data layer prevents cross-tenant access.

### Role Checking

Applications should check roles for UX purposes:

- Show/hide navigation items
- Enable/disable buttons
- Route to appropriate surfaces

But security enforcement happens at the data layer.

---

## When to Adopt

### Required For:

- All FORGE software projects
- Any project with user authentication
- Any project with stakeholder visibility

### Adoption Checklist

Before Phase 0 (Stand-Up) completes:

- [ ] Auth provider selected and configured
- [ ] Organization model implemented
- [ ] Membership with roles implemented
- [ ] At least one Owner account exists
- [ ] Stakeholder invitations can be sent
- [ ] RLS or equivalent enforces tenant isolation

---

## Integration Points

### With Stakeholder Interface

Auth/RBAC gates access to the Stakeholder Interface:
- Platform membership with `stakeholder` role required for portal access
- Stakeholder identity used for feedback attribution
- Platform context (not org context) scopes all portal content

See: [Stakeholder Interface](./stakeholder-interface.md)

### With FORGE Phases

Auth/RBAC is a **Phase 0 (Stand-Up)** concern:

```
Stand-Up (Phase 0)
├── Auth/RBAC deployed ← HERE
├── Stakeholder Interface deployed
└── Discovery running

Frame (Phase 1)
└── Stakeholders already logged in
```

### With Future Extensions

Auth/RBAC supports future capabilities:
- **Teams:** Sub-groups within organizations
- **Delegation:** Acting on behalf of others
- **SSO:** Federated identity
- **FAI-for-execution:** AI acting within user's permissions

These are explicitly deferred but the model supports them.

---

## Hard Boundaries

These constraints are non-negotiable:

| Boundary | Enforcement |
|----------|-------------|
| Platform/tenant separation | No plane mixing in sessions |
| Tenant isolation at data layer | RLS or equivalent required |
| Tenant roles scoped to membership | Never global tenant roles |
| Stakeholder is platform-level | Not a tenant role or boolean flag |
| Multi-role supported | Users may hold multiple tenant roles |
| Human manages access | No automatic role or membership assignment |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.1 | 2026-01-24 | Added platform vs tenant planes; stakeholder moved to platform level; added Dual-Plane Human Identity Pattern |
| 1.0 | 2026-01-23 | Initial Auth/RBAC extension definition |

---

*This extension is part of The FORGE Method(TM) — theforgemethod.org*
