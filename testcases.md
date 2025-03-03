# TEST CASES - Nginx with Keycloak Authentication

**Submitted By:** *(Your Name)*  
**Submitted To:** *(Reviewer’s Name)*  
**Test Case Version:** *1.0*  
**Reviewer Name:** *(Reviewer’s Name)*  

---

## Goal
The objective of this project is to set up **Nginx as a reverse proxy** and integrate it with **Keycloak for authentication**.  
- A user request is sent to **Nginx (Reverse Proxy)**.  
- Nginx **forwards the request to Keycloak** for authentication.  
- If authentication is successful, **Nginx forwards the request to the backend**.  
- If authentication fails, **Nginx returns an error or redirects the user to the login page**.  

---
# Environment Setup Test Cases  

## **TC1: Verify Podman Installation**  
**Scenario:** Ensure Podman is installed on the system.  

**Remarks:** Podman must be installed before setting up containers.  

**Given**  
- A Linux system with internet access.  

**When**  
- The user runs the command `podman --version`.  

**Then**  
- The system should display the installed Podman version.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of terminal output)*  

---

## **TC2: Verify Nginx Container Setup**  
**Scenario:** Ensure Nginx container is running in Podman.  

**Remarks:** Nginx must be properly installed and running.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs `podman run -d --name nginx -p 80:80 nginx`.  

**Then**  
- The container should start and be accessible via `http://localhost`.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of browser output or `podman ps` command)*  

---

## **TC3: Verify Keycloak Container Setup**  
**Scenario:** Ensure Keycloak is running in Podman.  

**Remarks:** Keycloak must be accessible for authentication.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs `podman run -d --name keycloak -p 8080:8080 quay.io/keycloak/keycloak`.  

**Then**  
- Keycloak should start and be accessible via `http://localhost:8080`.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of browser output or `podman ps` command)*  

---

## **TC4: Verify PostgreSQL Master and Slave Containers**  
**Scenario:** Ensure PostgreSQL master and slave are running.  

**Remarks:** Database must be configured correctly.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs commands to start PostgreSQL master and slave containers.  

**Then**  
- Both containers should be running and communicating properly.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste logs or `podman ps` output)*  

---

# Project Test Cases  

## **TC5: Verify Request is Forwarded to Keycloak**  
**Scenario:** Ensure Nginx forwards requests to Keycloak for authentication.  

**Remarks:** Authentication should happen through Keycloak.  

**Given**  
- A running Nginx and Keycloak setup.  

**When**  
- A user tries to access a protected endpoint via Nginx.  

**Then**  
- The request should be redirected to Keycloak for authentication.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste browser screenshot or Nginx logs)*  

---

## **TC6: Verify Authentication Success**  
**Scenario:** Ensure authenticated users can access the backend.  

**Remarks:** Users with valid credentials should proceed.  

**Given**  
- A valid user account in Keycloak.  

**When**  
- The user enters correct credentials in the login page.  

**Then**  
- The request is forwarded to the backend server.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste response message from backend)*  

---

## **TC7: Verify Authentication Failure**  
**Scenario:** Ensure incorrect login attempts are handled properly.  

**Remarks:** Users with incorrect credentials should be denied access.  

**Given**  
- A running Keycloak authentication setup.  

**When**  
- The user enters incorrect credentials.  

**Then**  
- The system should deny access and show an error message.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste error message screenshot)*  

---

## **TC8: Verify Redirection to Login Page**  
**Scenario:** Ensure unauthenticated users are redirected to login.  

**Remarks:** Users must authenticate before accessing the backend.  

**Given**  
- An unauthenticated user.  

**When**  
- The user tries to access a protected resource.  

**Then**  
- The system should redirect them to the login page.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste browser screenshot showing redirection)*  

---

# Non-Functional Requirement (NFR) Test Cases  

## **TC9: Performance Testing – Response Time**  
**Scenario:** Measure system response time under normal load.  

**Remarks:** The system should respond within acceptable limits.  

**Given**  
- Nginx, Keycloak, and backend services are running.  

**When**  
- A request is sent to the backend via Nginx.  

**Then**  
- The response time should be below a predefined threshold (e.g., <500ms).  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach response time logs from monitoring tools like `curl -w "%{time_total}"` or Apache JMeter results)*  

---

## **TC10: Security Testing – Unauthorized Access**  
**Scenario:** Ensure unauthorized users cannot access protected resources.  

**Remarks:** Unauthenticated requests should not bypass security.  

**Given**  
- A valid Keycloak authentication setup.  

**When**  
- A user tries to access a protected API endpoint without authentication.  

**Then**  
- The system should return a 401 Unauthorized error.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach API response or log screenshot)*  

---

## **TC11: Load Testing – Multiple Concurrent Users**  
**Scenario:** Ensure the system can handle multiple users simultaneously.  

**Remarks:** The system should be stable under load.  

**Given**  
- Nginx, Keycloak, and backend services are running.  

**When**  
- 100 concurrent users try to log in and access resources simultaneously.  

**Then**  
- The system should handle the load without crashes or performance degradation.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach logs or monitoring tool results like JMeter, Grafana, or Prometheus)*  

---

## **TC12: Reliability Testing – Service Uptime**  
**Scenario:** Ensure system availability over extended periods.  

**Remarks:** The system should remain stable without crashes.  

**Given**  
- All services are running for 24+ hours.  

**When**  
- The system is continuously monitored for downtime or failures.  

**Then**  
- There should be no unexpected crashes or downtime.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach monitoring tool screenshots from uptime trackers)*  

---

# Environment Setup Test Cases  

## **TC1: Verify Podman Installation**  
**Scenario:** Ensure Podman is installed on the system.  

**Remarks:** Podman must be installed before setting up containers.  

**Given**  
- A Linux system with internet access.  

**When**  
- The user runs the command `podman --version`.  

**Then**  
- The system should display the installed Podman version.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of terminal output)*  

---

## **TC2: Verify Nginx Container Setup**  
**Scenario:** Ensure Nginx container is running in Podman.  

**Remarks:** Nginx must be properly installed and running.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs `podman run -d --name nginx -p 80:80 nginx`.  

**Then**  
- The container should start and be accessible via `http://localhost`.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of browser output or `podman ps` command)*  

---

## **TC3: Verify Keycloak Container Setup**  
**Scenario:** Ensure Keycloak is running in Podman.  

**Remarks:** Keycloak must be accessible for authentication.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs `podman run -d --name keycloak -p 8080:8080 quay.io/keycloak/keycloak`.  

**Then**  
- Keycloak should start and be accessible via `http://localhost:8080`.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste screenshot of browser output or `podman ps` command)*  

---

## **TC4: Verify PostgreSQL Master and Slave Containers**  
**Scenario:** Ensure PostgreSQL master and slave are running.  

**Remarks:** Database must be configured correctly.  

**Given**  
- A system with Podman installed.  

**When**  
- The user runs commands to start PostgreSQL master and slave containers.  

**Then**  
- Both containers should be running and communicating properly.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste logs or `podman ps` output)*  

---

# Project Test Cases  

## **TC5: Verify Request is Forwarded to Keycloak**  
**Scenario:** Ensure Nginx forwards requests to Keycloak for authentication.  

**Remarks:** Authentication should happen through Keycloak.  

**Given**  
- A running Nginx and Keycloak setup.  

**When**  
- A user tries to access a protected endpoint via Nginx.  

**Then**  
- The request should be redirected to Keycloak for authentication.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste browser screenshot or Nginx logs)*  

---

## **TC6: Verify Authentication Success**  
**Scenario:** Ensure authenticated users can access the backend.  

**Remarks:** Users with valid credentials should proceed.  

**Given**  
- A valid user account in Keycloak.  

**When**  
- The user enters correct credentials in the login page.  

**Then**  
- The request is forwarded to the backend server.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste response message from backend)*  

---

## **TC7: Verify Authentication Failure**  
**Scenario:** Ensure incorrect login attempts are handled properly.  

**Remarks:** Users with incorrect credentials should be denied access.  

**Given**  
- A running Keycloak authentication setup.  

**When**  
- The user enters incorrect credentials.  

**Then**  
- The system should deny access and show an error message.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste error message screenshot)*  

---

## **TC8: Verify Redirection to Login Page**  
**Scenario:** Ensure unauthenticated users are redirected to login.  

**Remarks:** Users must authenticate before accessing the backend.  

**Given**  
- An unauthenticated user.  

**When**  
- The user tries to access a protected resource.  

**Then**  
- The system should redirect them to the login page.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Paste browser screenshot showing redirection)*  

---

# Non-Functional Requirement (NFR) Test Cases  

## **TC9: Performance Testing – Response Time**  
**Scenario:** Measure system response time under normal load.  

**Remarks:** The system should respond within acceptable limits.  

**Given**  
- Nginx, Keycloak, and backend services are running.  

**When**  
- A request is sent to the backend via Nginx.  

**Then**  
- The response time should be below a predefined threshold (e.g., <500ms).  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach response time logs from monitoring tools like `curl -w "%{time_total}"` or Apache JMeter results)*  

---

## **TC10: Security Testing – Unauthorized Access**  
**Scenario:** Ensure unauthorized users cannot access protected resources.  

**Remarks:** Unauthenticated requests should not bypass security.  

**Given**  
- A valid Keycloak authentication setup.  

**When**  
- A user tries to access a protected API endpoint without authentication.  

**Then**  
- The system should return a 401 Unauthorized error.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach API response or log screenshot)*  

---

## **TC11: Load Testing – Multiple Concurrent Users**  
**Scenario:** Ensure the system can handle multiple users simultaneously.  

**Remarks:** The system should be stable under load.  

**Given**  
- Nginx, Keycloak, and backend services are running.  

**When**  
- 100 concurrent users try to log in and access resources simultaneously.  

**Then**  
- The system should handle the load without crashes or performance degradation.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach logs or monitoring tool results like JMeter, Grafana, or Prometheus)*  

---

## **TC12: Reliability Testing – Service Uptime**  
**Scenario:** Ensure system availability over extended periods.  

**Remarks:** The system should remain stable without crashes.  

**Given**  
- All services are running for 24+ hours.  

**When**  
- The system is continuously monitored for downtime or failures.  

**Then**  
- There should be no unexpected crashes or downtime.  

**Test Run**  
**Date:** *(Enter date of test execution)*  

**Result:** *(Pass/Fail)*  

**Testing Outputs:** *(Attach monitoring tool screenshots from uptime trackers)*  

---

