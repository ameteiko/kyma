---
title: Exposing Functions
---

To access a Function within the cluster, use the `{function-name}.{namespace}.svc.cluster.local` endpoint, such as `test-function.default.svc.cluster.local`. To expose a Function outside the cluster, you must create an [APIRule custom resource (CR)](./00-custom-resources/apix-01-apirule.md):

![Expose a Function service](./assets/svls-api-rules.svg)

1. Create the APIRule CR where you specify the Function to expose, define an Oathkeeper Access Rule to secure it, and list which HTTP request methods you want to enable for it.

2. The API Gateway Controller detects a new APIRule CR and reads its definition.

3. The API Gateway Controller creates an Istio VirtualService and Access Rules according to details specified in the CR. Such a Function service is available under the `{host-name}.{domain}` endpoint, such as `my-function.kyma.local`.

This way you can specify multiple APIRules with different authentication methods for a single Function service.

>**TIP:** See the [tutorial](../03-tutorials/00-serverless/svls-03-expose-function.md) for a detailed example.
