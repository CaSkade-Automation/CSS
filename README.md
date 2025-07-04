# CSS-Ontology
An ontology containing the definitions of the Capability, Skill and Service (CSS) reference model of Plattform Industrie 4.0. The model is presented in this [whitepaper](https://www.plattform-i40.de/IP/Redaktion/EN/Downloads/Publikation/CapabilitiesSkillsServices.html). Extensions were later added in a [follow-up whitepaper](https://www.plattform-i40.de/IP/Redaktion/DE/Downloads/Publikation/2025-i40-capabilities.pdf?__blob=publicationFile&v=5). There is also a scientific publication about the CSS reference model in case you want to cite this work: https://www.degruyter.com/document/doi/10.1515/auto-2022-0117/html.

## Overview
This is an ontology implementation of the CSS reference model as defined by [this Plattform Industrie 4.0 Whitepaper](https://www.plattform-i40.de/IP/Redaktion/DE/Downloads/Publikation/CapabilitiesSkillsServices.html). All definitions according to this whitepaper can be found in a [Wiki page](https://github.com/hsu-aut/css-ontology/wiki/Definitions). The most important elements of this reference model are:

### Capability
A *Capability* is an implementation-independent specification of a function in industrial production to achieve an effect in the physical or virtual world. A *Capability* may be implemented by one or more *Skills*.
You can think of a capability as a machine-interpretable description of a function. Such a description typically features *Properties* and constraints on these properties.

### Skill
A *Skill* is an executable implementation of an encapsulated (automation) function specified by a *Capability*. Every *Skill* needs to have a *SkillInterface* (e.g. an OPC UA server) that allows external control of a *Skill*.

### Service
A *Service* is a description of the commercial aspects and means of provision of offered *Capabilities*. A service may be considered as a wrapper around a capability that adds additional information, typically when one wants to offer or request capabilities via a marketplace.

## Additional Resources
<p align="center">
<img src="https://github.com/hsu-aut/css-ontology/blob/documentation/images/images/CSS-Architecture_CSS-Mark.jpg?raw=true" width="800" title="CSS Architecture">
</p>
This is just a rather abstract ontology containing only the most important terms and relations. In order to model capabilities on a more detailed level as well as executable skills with all necessary information, there are extensions to this ontology on two levels:

- [CaSk](https://github.com/hsu-aut/cask) is an ontology that adds additional details (e.g., a state machine) while still staying extensible so that domain-specific ontologies can built on CaSk
- On an even more detailed level, there are currently two domain-specific ontologies that can be used to model capabilities and skills on a very detailed level:
  - The [CaSkMan ontology](https://github.com/aljoshakoecher/caskman) can be used to model capabilities and skills in manufacturing. It extends CaSk by standards such as DIN 8580 (manufacturing operations), VDI 2860 (handling operations) as well as WADL and OPC UA to model skills with interfaces based on web services as well as OPC UA.
  - [RoboCaSk](https://github.com/Miguel2617/robocap) is an ontology for capabilities and skills of autonomous systems that can work collaboratively to achieve a common goal. It extends CaSk by additional elements to represent such systems and thei skill interfaces.

## Ontology example
Detailed examples can be found in the two repositories of  [CaSkMan](https://github.com/aljoshakoecher/caskman) and [RoboCaSk](https://github.com/Miguel2617/robocap)

## Current Issues
Here are some known issues that were found while creating this ontology:
- There is an object property `offersUseOf`, which is used to connect a ServiceProvider with the Services it offers. In addition to `offersUseOf`, there is another object property `offers`, which connects a service with the capability it "embeds". This is a bit confusing. `offersUseOf` sounds like a sub property of `offers` but it is in fact something totally different.
The property `offers` should be changed, because a service doesn't "offer" anything actively. Maybe "contains" or "containsUseOf" would be better?

- `hasInput` and `isInputFor` sound like inverse object properties, but they are in fact totally different properties.
