**Issue**: The cameras should contain a tiny healthcheck to ensure they are operational. Damaged cameras can be removd from the central registry (ADR-007).

**Decision**: A basic health check will be implemented on the cameras for monitoring.

**Constraints**: None

**Implications**: Implementing an API will require additional infrastructure such as API Gateway/WAF, and also increase attack vectors.

**Group**: Infrastructure

**Positions**: Implement the business logic on the mobile app itself.

**Argument**: Hosting logic in the API Gateway will allow for easier management and deployment of code (a single applicaiton hosting an API instead of hundreds of mobile apps).
