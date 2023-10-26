
**Issue**: The mobile app will have the ability to connect to any of several hundred cameras. There needs to be a data store of these cameras and their connectivity details for the API and thus mobile app to connect to.

**Decision**: We need a central registry, which will be a database on Azure SQL, under a bounded context for "Site Management".

**Constraints**: None

**Implications**: Implementing an Azure SQL instance will induce implications for considerations such as monitoring and backup/recovery.

**Group**: Infrastructure

**Positions**: N/A

**Argument**: Having a central registry will allow for easy discovery of cameras. Camera's which fail a health probe will eventually be removed or marked as "stale".


We feel a database will add business value to the core domain, despite being a significant infrastructure change.