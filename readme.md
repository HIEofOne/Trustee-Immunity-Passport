# Trustee Immunity Passport Product Sprint

## About Trustee

Trustee gives people control over how their health records and information are used. The Trustee Directory™ enables patient communities, institutions, researchers, and other organizations to aggregate and analyze participant data if a patient has granted authorization or access. This unique feature benefits the wider health ecosystem while protecting individual patient privacy.

## Why Use Trustee?

The development of contact tracing and other symptom reporting apps has exploded under the pandemic. In order to leverage this groundswell of support, Trustee aims to make every single one of those apps a part of a useful whole. Trustee is a standards based solution which allows the data you collect to extend beyond your app into a global view of the pandemic, while assuring that each of your users has visibility and control over their own PI. Trustee is focused on leveraging the whole emerging community of symptom and health reporting toward the global need, creating value for its users beyond that of any individual piece of software.

## Sprint Overview

The intention of this sprint is to help developers who are working on symptom reporting and contact tracing (SRCT) apps to learn how Trustee and the Trustee Directory can enable their products to be part of a larger reporting ecosystem, and also to serve group policies to enable the distribution of patient data as a component toward developing a solution to allow people to “go back to work and school again” during the next stage of the current pandemic.

## Standards Based Reporting

Standards are crucial to support the network effect that is essential to SRCT apps. If we expect patients to share their health data broadly in order to understand and address the problems in a pandemic, we must be working within a common set of agreements as developers and clinicians to keep trust levels high and explanations as simple as possible. It is easy to see where problems could arise inside of an ecosystem which is not standards based. As such, using commonly held standards to promote patient trust and opt-in is a must have.

## The NOSH Patient Record

NOSH is an open source patient record which is currently being used to serve the clinician forms in the current Trustee workflow. In the context of this sprint, it is a passive component that absorbs data, and completes the clinician portion of the Immunity Passport interaction.

## Trustee Directory and Policies

In the Trustee model, the patient chooses from a set of available policies how their personal information will be shared. Additional to policy choosing, there is also a transactional authorization by the patient that can be leveraged in cases where the policies do not allow automated opt-in. The available policies are designed and published by public health experts and consistently displayed by Trustee in the same way that single sign-on (SSO) systems like Google, provide a consistent display of information sharing requests. Trustee uses OAuth and other standards established for SSO to enable large scale data usage and promote the network effect essential to pandemic mitigation. By using Trustee (at the individual level) in combination with Trustee Directory policies (at the community level), developers can offload the problem of authorization for dissemination of the data which their SRCT apps collect. This can help to both streamline the development process and also exponentially multiply the value of the data each individual app collects.

## Standard Authorization Flow

The patient-level Trustee uses a standard OAuth flow and optional UMA extensions to OAuth along with familiar OpenID Connect and emerging self-sovereign (blockchain) identifier methods. Applications make calls to display the uniformly defined policies to patients and receive data use authorization through each patient’s individual Trustee account. The default policies for an individual Trustee are suggested by the Trustee Directory operator. The independence of the Trustee Directory operators builds trust and promotes individual participation, effectively driving the network effect as more people opt-in to more uses of their personal data.

## Trustee Signup

Patients get their Trustee in one of three ways:
* A In a “white label” presentation linked to a SRCT app
* B In a group “call to action” scenario, as through a community or company website that might also offer their constituents a choice of compatible apps.
* C As an a la carte service paid by the individual independent of any particular app

In each of these three scenarios, the patient is assured personal control and tracking of how their information is stored and shared. In all three, the patient is presented with a set of commonly held policies and default settings as suggested by in the Trustee Directory to opt in and out of, much like a GDPR compliant cookie warning appears to end users during a visit to a corporate website.

## Deployment

As an SRCT app developer, you start off by creating a minimal Trustee Directory installation (A, above) and at least one Trustee account for testing. Deployment instructions are as follows:

[Insert steps here]
