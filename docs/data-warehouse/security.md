---
title: Security for data warehousing
description: Learn more about securing the SQL Endpoint and Warehouse in Microsoft Fabric.
author: cynotebo
ms.author: cynotebo
ms.reviewer: wiassaf
ms.date: 05/23/2023
ms.topic: overview
ms.custom: build-2023
ms.search.form: Warehouse roles and permissions # This article's title should not change. If so, contact engineering.
---
# Security for data warehousing in Microsoft Fabric

**Applies to:** [!INCLUDE[fabric-se-dw](includes/applies-to-version/fabric-se-and-dw.md)]

This article covers security topics for securing the [!INCLUDE [fabric-se](includes/fabric-se.md)] of the lakehouse and the [!INCLUDE [fabric-dw](includes/fabric-dw.md)] in [!INCLUDE [product-name](../includes/product-name.md)].

[!INCLUDE [preview-note](../includes/preview-note.md)]

For information on [!INCLUDE [product-name](../includes/product-name.md)] security, see [Security in Microsoft Fabric](../security/security-overview.md).

For information on connecting to the [!INCLUDE [fabric-se](includes/fabric-se.md)] and [!INCLUDE [fabric-dw](includes/fabric-dw.md)], see [Connectivity](connectivity.md).

## Warehouse access model

[!INCLUDE [product-name](../includes/product-name.md)] permissions and granular SQL permissions work together to govern Warehouse access and the user permissions once connected. 
- Warehouse connectivity is dependent on being granted the [!INCLUDE [product-name](../includes/product-name.md)] Read permission, at a minimum, for the Warehouse.
- [!INCLUDE [product-name](../includes/product-name.md)] item permissions enable the ability to provide a user with SQL permissions, without needing to grant those permissions within SQL.
-  [!INCLUDE [product-name](../includes/product-name.md)] workspace roles provide [!INCLUDE [product-name](../includes/product-name.md)] permissions for all warehouses within a workspace.
-  Granular user permissions can be further managed via T-SQL.

### Workspace roles

Workspace roles are used for development team collaboration within a workspace. Role assignment determines the actions available to the user and applies to all items within the workspace.
- For an overview of [!INCLUDE [product-name](../includes/product-name.md)] workspace roles, see [Roles in workspaces](../get-started/roles-workspaces.md).
- For instructions on assigning workspace roles, see [Give Workspace Access](../get-started/give-access-workspaces.md).

See [Workspace roles in Fabric data warehousing](workspace-roles.md) for details on the specific Warehouse capabilities provided through Workspace roles.

### Object-level security

Workspace roles and item permissions provide an easy way to assign coarse permissions to a user for the entire warehouse. However, in some cases, more granular permissions are needed for a user. To achieve this, standard T-SQL constructs can be used to provide specific permissions to users.

See [SQL granular permissions](sql-granular-permissions.md) for details on the managing granular permissions in SQL.

### Guidance

When evaluating the permissions to assign to a user, consider the following guidance:

- Only team members who are currently collaborating on the solution should be assigned to Workspace roles (Admin, Member, Contributor), as this provides them access to all Items within the workspace. 
- If they primarily require read only access, assign them to the Viewer role and grant read access on specific objects through T-SQL.  For more information, see [Manage SQL granular permissions](sql-granular-permissions.md).
- If they are higher privileged users, assign them to Admin, Member or Contributor roles. The appropriate role is dependent on the other actions that they will need to perform.  
- Other users, who only need access to an individual warehouse or require access to only specific SQL objects, should be given Fabric Item permissions and granted access through SQL to the specific objects. 
- You can manage permissions on Azure Activity Directory groups, as well, rather than adding each specific member.

## Next steps

- [Connectivity](connectivity.md)
