project exectuable in files
1. Project Overview

This project introduces a safety mechanism within an application (e.g., admin panel, incident management system) to prevent the deletion of user accounts that are still actively assigned to incidents. It ensures data integrity, maintains accountability, and avoids orphaned records in incident logs.


---

🔷 2. Background and Importance

In many applications, users (especially employees, operators, agents, etc.) are assigned to handle or resolve incidents—which could be support tickets, maintenance reports, alerts, or crisis events.

Without proper checks:

If a user is deleted while being assigned to an active or historical incident,

The incident may lose traceability (who handled it?)

Reports and workflows can become incomplete or corrupted


Hence, deletion of such users must be blocked until they are unassigned.


---

🔷 3. Objectives

✅ Prevent deletion of any user who is currently assigned to one or more incidents.

✅ Maintain referential integrity in the database.

✅ Provide meaningful feedback to the admin/user performing the deletion.

✅ Ensure incidents remain auditable and valid.



---

🔷 4. Functional Requirements

1. Check Before Deletion

When a delete request is triggered for a user, the system checks:

Are there any incidents assigned to this user?

Are they active or unresolved?
2. Block Deletion

If any incidents are found:

Cancel the deletion.

Show an error: “User cannot be deleted because they are assigned to active incidents.”
3. Allow Safe Deletion

If no incidents are linked or all are resolved:

Proceed with deletion safely.
