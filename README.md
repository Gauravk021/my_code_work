Build was failing due to an invalid Docker base image tag (jdk:17.0.18-98-rc) which was not available in the registry.

Identified the issue from CloudBees logs (“image not found”). Updated the Dockerfile to use a valid JDK image version (jdk:17.0.18).

Post change, pushed the code and CI pipeline auto-triggered. Verified that the latest build (#14) completed successfully.