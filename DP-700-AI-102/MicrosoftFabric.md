# Microsoft Fabric Topics

---

# Is it possible to move a Fabric Capacity from a subscription to another? [Perplexity]

Yes, it is possible in principle, but it is not a simple “one-click move and everything stays identical” scenario. Azure supports moving resources between subscriptions in the same tenant, and Fabric Multi-Geo lets you create capacities in a chosen region, but the capacity remains tied to the region where it was created unless you recreate or move the workload in a supported way.

## What applies to your case

If you create the Fabric capacity in 2911-FAB-002-PRD-CO in West Germany, 
moving that same capacity to 1615-FAB-001-PRD-NC in West Europe is only 
feasible if the move is supported for that resource and both subscriptions 
are in the same Entra tenant.

However, a region change is the real complication: 

Fabric guidance says that to change region for existing content, the normal 
approach is to create a new capacity in the target region and move workspaces 
to it, or temporarily use shared capacity and then move to the new capacity.

## Practical answer

So the answer is:

- Same tenant, different subscription: 

usually possible for Azure resource moves in general.

- Different Azure regions: 

not a “capacity relocation” in the clean sense; 
Microsoft’s Fabric guidance points to recreate in the target region 
and move workspaces/content.

- West Germany to West Europe: 

this is especially sensitive because it crosses regions, so you should 
assume migration is required, not just a subscription rename or transfer.

## Catches to watch

- Region-bound content. 

Fabric content remains in the region of the capacity where it lives, and 
moving it can affect storage, refresh, and availability.

- Non-Power BI Fabric items. 

Microsoft notes that workspaces with non-Power BI Fabric items cannot be 
moved between regions unless those items are removed first.

- Large-storage semantic models. 

These should not be moved away from the region where they were created; 
Microsoft warns they may fail to load after a region move.

- Downtime/refresh impact. 

During workspace migration, publishing and scheduled refresh can fail temporarily, 
so plan a maintenance window.

- Tenant and compliance. 

Azure resource moves do not support moving to a different Entra tenant, and 
compliance/data-residency rules still apply.

### Difficulty level

I’d rate it as doable but non-trivial. 

If you only need to change the billing/subscription owner and stay in the same region, 
it may be relatively straightforward; if you also need to go from West Germany to West Europe, 
treat it as a migration project with validation, not a simple move.

### Recommended approach

For a PoC, your current plan to reuse the existing connected subscription is reasonable if 
the region is acceptable. If the project later needs a dedicated subscription in West Europe, 
the safest path is to create a new capacity in West Europe and reassign workspaces, rather 
than relying on a future “move the whole capacity” operation.

---

# Is it possible to move a Fabric Capacity from a subscription to another? [Gemini]

Yes — in many cases you can move a Fabric capacity to another Azure subscription, 
**but only within the same tenant and with the usual Azure resource-move constraints**. 

Microsoft community guidance and user reports indicate that the Azure portal exposes 
a Move to another subscription action for Fabric capacity resources, while the practical 
requirement is to plan the change carefully and verify the capacity and attached workspaces 
afterward.

## What this means

The capacity itself is the resource you move; you do not usually “move Fabric” as a 
whole environment in one step. Workspaces can then remain assigned to that capacity, 
or you can reassign them separately if needed.

## Important constraints

The move is not a cross-tenant transfer, and it is not the same as migrating content 
between capacities or regions. 

If your workspaces or semantic models depend on region-specific behavior, you still 
need to validate them after the subscription move.

## Practical approach

A safe sequence is to:

1. Check that both subscriptions are in the same tenant.
2. Schedule a maintenance window.
3. Stop or pause use of the capacity if appropriate.
4. Move the capacity in Azure.
5. Confirm that workspaces still function correctly on the new subscription.

## Related note

If your real goal is to change where workloads run, sometimes the better operation 
is to reassign workspaces to another Fabric capacity rather than moving the capacity
resource itself.

---

# Is it possible to move a Fabric Capacity from a subscription to another? [Gemini]

Directly moving a Microsoft Fabric Capacity as an object from one Azure subscription to another 
is not supported. 

A Fabric capacity is permanently tied to the region and subscription where it was created.

However, you can accomplish your goal by creating a new capacity in your target subscription and reassigning your workspaces.

## How to Migrate Your Workspaces

Follow these steps to move your Fabric workloads to the new subscription:

1. Set up the Target Capacity

Purchase and provision a new Fabric capacity in your destination Azure subscription. 
**Ensure the new capacity is in the same region as the original if you are hosting data there!**.

2. Reassign Workspaces

Once the new capacity is active, use the `Microsoft Fabric Admin Portal` to assign your 
workspaces to the newly created capacity:

- Go to Settings > Admin portal > Capacity settings.

- Select your new capacity and use the Assign workspaces option to move them in bulk.

- Alternatively, individual Workspace Admins can change the capacity directly in the Workspace Settings under the License Info tab.

3. Copy Capacity Settings

Manually replicate any specific settings from the old capacity to the new one, 
such as tenant settings, Power BI workloads, and Data Engineering/Science configurations.

4. Decommission the Old Capacity

Once all workloads are verified in the new subscription, delete the original Fabric 
capacity in your old Azure subscription to avoid incurring further charges.

---