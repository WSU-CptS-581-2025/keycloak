diff --git a/README.md b/README.md
index c9856046d4..e69de29bb2 100644
--- a/README.md
+++ b/README.md
@@ -1,80 +0,0 @@
-![Keycloak](https://github.com/keycloak/keycloak-misc/blob/main/logo/logo.svg)
-
-![GitHub Release](https://img.shields.io/github/v/release/keycloak/keycloak?label=latest%20release)
-[![OpenSSF Best Practices](https://bestpractices.coreinfrastructure.org/projects/6818/badge)](https://bestpractices.coreinfrastructure.org/projects/6818)
-[![CLOMonitor](https://img.shields.io/endpoint?url=https://clomonitor.io/api/projects/cncf/keycloak/badge)](https://clomonitor.io/projects/cncf/keycloak)
-[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/keycloak/keycloak/badge)](https://securityscorecards.dev/viewer/?uri=github.com/keycloak/keycloak)
-[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/keycloak-operator)](https://artifacthub.io/packages/olm/community-operators/keycloak-operator)
-![GitHub Repo stars](https://img.shields.io/github/stars/keycloak/keycloak?style=flat)
-![GitHub commit activity](https://img.shields.io/github/commit-activity/m/keycloak/keycloak)
-[![Translation status](https://hosted.weblate.org/widget/keycloak/svg-badge.svg)](docs/translation.md)
-
-# Open Source Identity and Access Management
-
-Add authentication to applications and secure services with minimum effort. No need to deal with storing users or authenticating users.
-
-Keycloak provides user federation, strong authentication, user management, fine-grained authorization, and more.
-
-
-## Help and Documentation
-
-* [Documentation](https://www.keycloak.org/documentation.html)
-* [User Mailing List](https://groups.google.com/d/forum/keycloak-user) - Mailing list for help and general questions about Keycloak
-* Join [#keycloak](https://cloud-native.slack.com/archives/C056HC17KK9) for general questions, or [#keycloak-dev](https://cloud-native.slack.com/archives/C056XU905S6) on Slack for design and development discussions, by creating an account at [https://slack.cncf.io/](https://slack.cncf.io/).
-
-
-## Reporting Security Vulnerabilities
-
-If you have found a security vulnerability, please look at the [instructions on how to properly report it](https://github.com/keycloak/keycloak/security/policy).
-
-
-## Reporting an issue
-
-If you believe you have discovered a defect in Keycloak, please open [an issue](https://github.com/keycloak/keycloak/issues).
-Please remember to provide a good summary, description as well as steps to reproduce the issue.
-
-
-## Getting started
-
-To run Keycloak, download the distribution from our [website](https://www.keycloak.org/downloads.html). Unzip and run:
-
-    bin/kc.[sh|bat] start-dev
-
-Alternatively, you can use the Docker image by running:
-
-    docker run quay.io/keycloak/keycloak start-dev
-    
-For more details refer to the [Keycloak Documentation](https://www.keycloak.org/documentation.html).
-
-
-## Building from Source
-
-To build from source, refer to the [building and working with the code base](docs/building.md) guide.
-
-
-### Testing
-
-To run tests, refer to the [running tests](docs/tests.md) guide.
-
-
-### Writing Tests
-
-To write tests, refer to the [writing tests](docs/tests-development.md) guide.
-
-
-## Contributing
-
-Before contributing to Keycloak, please read our [contributing guidelines](CONTRIBUTING.md). Participation in the Keycloak project is governed by the [CNCF Code of Conduct](https://github.com/cncf/foundation/blob/main/code-of-conduct.md).
-
-Joining a [community meeting](https://www.keycloak.org/community) is a great way to get involved and help shape the future of Keycloak.
-
-## Other Keycloak Projects
-
-* [Keycloak](https://github.com/keycloak/keycloak) - Keycloak Server and Java adapters
-* [Keycloak QuickStarts](https://github.com/keycloak/keycloak-quickstarts) - QuickStarts for getting started with Keycloak
-* [Keycloak Node.js Connect](https://github.com/keycloak/keycloak-nodejs-connect) - Node.js adapter for Keycloak
-
-
-## License
-
-* [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
diff --git a/js/apps/admin-ui/cypress/support/pages/admin-ui/manage/authentication/FlowDetail.ts b/js/apps/admin-ui/cypress/support/pages/admin-ui/manage/authentication/FlowDetail.ts
index 39e4854048..3b049f2d62 100644
--- a/js/apps/admin-ui/cypress/support/pages/admin-ui/manage/authentication/FlowDetail.ts
+++ b/js/apps/admin-ui/cypress/support/pages/admin-ui/manage/authentication/FlowDetail.ts
@@ -60,7 +60,7 @@ export default class FlowDetails {
   }
 
   addExecution(subFlowName: string, executionTestId: string) {
-    this.#clickEditDropdownForFlow(subFlowName, "Add step");
+    this.#clickEditDropdownForFlow(subFlowName, "Add execution");
 
     cy.get(".pf-v5-c-pagination").should("exist");
     cy.findByTestId(executionTestId).click();
@@ -93,7 +93,7 @@ export default class FlowDetails {
 
   #fillSubFlowModal(subFlowName: string, name: string) {
     cy.get(".pf-v5-c-modal-box__title-text").contains(
-      "Add step to " + subFlowName,
+        "Add sub-flow to " + subFlowName,
     );
     cy.findByTestId("name").type(name);
     cy.findByTestId("modal-add").click();
diff --git a/js/apps/admin-ui/maven-resources/theme/keycloak.v2/admin/messages/messages_en.properties b/js/apps/admin-ui/maven-resources/theme/keycloak.v2/admin/messages/messages_en.properties
index 9f82c341ed..f2ac5e8d46 100644
--- a/js/apps/admin-ui/maven-resources/theme/keycloak.v2/admin/messages/messages_en.properties
+++ b/js/apps/admin-ui/maven-resources/theme/keycloak.v2/admin/messages/messages_en.properties
@@ -1998,7 +1998,7 @@ principalAttributeHelp=Name or Friendly Name of the attribute used to identify e
 nameIdPolicyFormat=NameID policy format
 idpInitiatedSsoUrlName=IDP-Initiated SSO URL name
 selectMethod=Select method
-deleteConfirmExecution=Delete execution?
+deleteConfirmExecution=Delete flow {{name}}?
 eventTypes.VALIDATE_ACCESS_TOKEN_ERROR.name=Validate access token error
 xFrameOptions=X-Frame-Options
 scopeDescriptionHelp=Description of the client scope
@@ -3412,4 +3412,8 @@ authorizationScope.Groups.manage-members=Manages group members
 authorizationScope.Groups.manage-membership=Adds or removes group members
 authorizationScope.Groups.view=Views this group
 authorizationScope.Groups.view-members=Views group members
-authorizationScope.IdentityProviders.token-exchange=Allows clients to exchange tokens for  tokens issued by this identity provider
\ No newline at end of file
+authorizationScope.IdentityProviders.token-exchange=Allows clients to exchange tokens for  tokens issued by this identity provider
+evaluation=Evaluation
+addSubFlowTo=Add sub-flow to {{name}}
+addExecutionTo=Add execution to {{name}}
+addConditionTo=Add condition to {{name}}
\ No newline at end of file
diff --git a/js/apps/admin-ui/src/authentication/FlowDetails.tsx b/js/apps/admin-ui/src/authentication/FlowDetails.tsx
index c03f1c3444..2e128f2d1e 100644
--- a/js/apps/admin-ui/src/authentication/FlowDetails.tsx
+++ b/js/apps/admin-ui/src/authentication/FlowDetails.tsx
@@ -222,7 +222,9 @@ export default function FlowDetails() {
   };
 
   const [toggleDeleteDialog, DeleteConfirm] = useConfirmDialog({
-    titleKey: "deleteConfirmExecution",
+    titleKey: t("deleteConfirmExecution", {
+      name: selectedExecution?.displayName,
+    }),
     children: (
       <Trans i18nKey="deleteConfirmExecutionMessage">
         {" "}
@@ -386,7 +388,7 @@ export default function FlowDetails() {
                     variant="secondary"
                     onClick={() => setShowAddExecutionDialog(true)}
                   >
-                    {t("addStep")}
+                    {t("addExecution")}
                   </Button>
                 </ToolbarItem>
                 <ToolbarItem>
diff --git a/js/apps/admin-ui/src/authentication/components/AddFlowDropdown.tsx b/js/apps/admin-ui/src/authentication/components/AddFlowDropdown.tsx
index e727687fc7..3aba6c5492 100644
--- a/js/apps/admin-ui/src/authentication/components/AddFlowDropdown.tsx
+++ b/js/apps/admin-ui/src/authentication/components/AddFlowDropdown.tsx
@@ -75,7 +75,7 @@ export const AddFlowDropdown = ({
                 setType(providerId === "form-flow" ? "form" : "basic")
               }
             >
-              {t("addStep")}
+              {t("addExecution")}
             </DropdownItem>
             <DropdownItem
               key="addCondition"
diff --git a/js/apps/admin-ui/src/authentication/components/modals/AddStepModal.tsx b/js/apps/admin-ui/src/authentication/components/modals/AddStepModal.tsx
index 819eb704c9..1a5681b300 100644
--- a/js/apps/admin-ui/src/authentication/components/modals/AddStepModal.tsx
+++ b/js/apps/admin-ui/src/authentication/components/modals/AddStepModal.tsx
@@ -105,7 +105,11 @@ export const AddStepModal = ({ name, type, onSelect }: AddStepModalProps) => {
     <Modal
       variant={ModalVariant.medium}
       isOpen={true}
-      title={t("addStepTo", { name })}
+      title={
+        type == "condition"
+            ? t("addConditionTo", { name })
+            : t("addExecutionTo", { name })
+      }
       onClose={() => onSelect()}
       actions={[
         <Button
diff --git a/js/apps/admin-ui/src/authentication/components/modals/AddSubFlowModal.tsx b/js/apps/admin-ui/src/authentication/components/modals/AddSubFlowModal.tsx
index 5c7884530f..be4c13ffcb 100644
--- a/js/apps/admin-ui/src/authentication/components/modals/AddSubFlowModal.tsx
+++ b/js/apps/admin-ui/src/authentication/components/modals/AddSubFlowModal.tsx
@@ -58,7 +58,7 @@ export const AddSubFlowModal = ({
   return (
     <Modal
       variant={ModalVariant.medium}
-      title={t("addStepTo", { name })}
+      title={t("addSubFlowTo", { name })}
       onClose={onCancel}
       actions={[
         <Button
