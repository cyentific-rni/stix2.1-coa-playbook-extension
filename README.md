## A STIX 2.1 Extension Definition for Sharing Machine-Readable Security Playbooks and Orchestration Workflows via the Course of Action SDO

**This repository includes a STIX 2.1 nested property extension that augments the Course of Action (COA) STIX Domain Object (SDO) type to enable describing, embedding, storing, managing, and sharing cybersecurity playbooks and orchestration workflows**. 

The decision to extend the Course of Action SDO was based on the facts that the terms security playbook and course of action are semantically very close (i.e., security playbook can be a subclass of course of action) and that extending an object allows making use of the existing specification-defined relationships, such as the ones between the Course of Action and other objects.

![](https://github.com/fovea-research/stix2.1-coa-playbook-extension/blob/main/images/STIX2.1-nested-property-extension.jpg)

The illustration above concisely explains what comprises an Extension Definition. The blue rectangles represent an instance of a COA SDO type with an extension. The red rectangle represents the associated Extension Definition object that provides information about the new or extended object type. The amber rectangle captures the normative definition of the extension, and it is a JSON schema.

### Reading Material

A technical report that explains in detail the extension can be found at https://arxiv.org/abs/2203.04136. 

**Please note that the authoritative source of this work is this Github repository and its [README.md](https://github.com/fovea-research/stix2.1-coa-playbook-extension#readme) file and not the technical report mentioned above and uploaded on arxiv.** The report is not going to be updated and is only provided as a reference material that includes background information. 

### Extension Definition Related Files:
- [Example Instances](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/examples)
- [Extension Definition Object](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/extension-definition)
- [Normative Definition of the Extension - JSON Schema](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/schema)

### Properties that Comprise the Nested Property Extension of the COA SDO to Support Sharing Machine-Readable Security Playbooks
| Property Name | Data Type | Description |
| :--- | :--- |:--- |
| **extension_type** (required) | `string` | The value of this property **MUST** be `property-extension`. |
| **playbook_id** (optional)| `string` | A value that (uniquely) identifies the playbook. If the playbook itself embeds an identifier then the playbook_id SHOULD use the same identifier (value) for correlation purposes.|
| **description** (optional)| `string` | An explanation, details, and more context about what this playbook does and tries to accomplish. |
| **created** (required)| `timestamp` | The time at which the playbook extension (instance) was created. This may be different than the time at which the "parent" Course of Action object instance was created. |
| **modified** (required)| `timestamp` | The time at which the playbook extension (instance) was last modified. A modification in the extension requires updating the property **modified** in both the extension and the “parent” Course of Action object. |
| **revoked** (optional)| `boolean` | A boolean that identifies if the playbook extension (instance) is no longer valid. |
| **playbook_creation_time** (optional)| `timestamp` | The time at which the playbook was originally created. |
| **playbook_modification_time** (optional)| `timestamp` | The time at which the playbook was last modified. |
| **playbook_valid_from** (optional)| `timestamp` | The time from which the playbook is considered valid and the steps that it contains can be executed. |
| **playbook_valid_until** (optional)| `timestamp` | The time from which the playbook should no longer be considered a valid playbook to be executed. |
| **playbook_creator** (optional)| `identifier` | The identifier of the entity that created the playbook. |
| **labels** (optional)| `list` of type `string` | A set of labels for the playbook (e.g., adversary persona names, associated groups, or malware family/variant/name that this playbook is related to). |
| **organization_type** (optional)| `list` of type `open-vocab` | The type of organization that the playbook is intended for. The value for this property **SHOULD** come from the `industry-sector-ov` open vocabulary as defined in STIX Version 2.1.|
| **playbook_standard** (optional)| `string` | The standard/format/notation the playbook conforms to (e.g., CACAO, BPMN). |
| **playbook_abstraction** (optional)| `open-vocab` | The playbook’s level of abstraction (with regards to consumption). Open Vocabulary: `[template, executable]` |
| **playbook_type** (optional)| `list` of type `open-vocab` | A list of playbook types that specifies the operational roles this playbook addresses. The open vocabulary is based on the available options in the CACAO standard and NIST SP 800-61 rev2. Open Vocabulary: `[notification, detection, investigation, prevention, mitigation, remediation, analysis, containment, eradication, recovery, attack]` |
| **playbook_impact** (optional)| `integer` | From 0 to 100, an integer representing the impact the playbook has on the organization. A value of 0 means specifically undefined. Impact values range from 1, the lowest impact, to a value of 100, the highest. For example, a purely investigative playbook that is non-invasive could have a low impact value of 1. In contrast, a playbook that performs changes such as adding rules into a firewall should have a higher impact value. |
| **playbook_severity** (optional)| `integer` | From 0 to 100, an integer representing the seriousness of the conditions that this playbook addresses. A value of 0 means specifically undefined. Severity values range from 1, the lowest severity, to a value of 100, the highest. |
| **playbook_priority** (optional)| `integer` | From 0 to 100, an integer representing the priority of this playbook relative to other defined playbooks. A value of 0 means specifically undefined. Priority values range from 1, the highest priority, to a value of 100, the lowest. This property can support addressing different use cases and requirements of a producing or consuming entity. For example, a STIX 2.1 COA object that embeds more than one playbook can use this property to define a priority with regards to which one should be executed. |
| **playbook_bin** (optional)| `binary` | The entire playbook encoded in base64. Security playbook producers and consumers use this property to share and retrieve entire playbooks.



## Maintainers
- [Vasileios-Mavroeidis](https://github.com/Vasileios-Mavroeidis)

- [Mateusz Zych](https://www.linkedin.com/in/mateuszzych/)
