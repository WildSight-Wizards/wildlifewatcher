
**Issue**: Over time, our architecture and compliance to the characteristics can erode. We need a mechanism to ensure we comply with these characteristics, over time.

**Decision**: In line with our affordability, we will use Azure native monitoring. This consists of Azure Monitor + App Insights.

**Constraints**: None

**Implications**: Time will be required to catalog services and their business criticality, as well as SLOs, and recipients of alerts.

**Group**: Infrastructure

**Positions**: N/A

**Argument**: Having a central registry will allow for easy discovery of cameras. Camera's which fail a health probe will eventually be removed or marked as "stale".

