**Issue**: Deploying an API to host our business logic, will create significant changes in our infrastructure and pose new challenges.

**Decision**: Logic to connect to and manage cameras should be in one place, thus an API will host and manage this business logic.

**Constraints**: None

**Implications**: Implementing an API will require additional infrastructure such as API Gateway/WAF, and also increase attack vectors.

**Group**: Infrastructure

**Positions**: Implement the business logic on the mobile app itself.

**Argument**: Hosting logic in the API Gateway will allow for easier management and deployment of code (a single applicaiton hosting an API instead of hundreds of mobile apps).
