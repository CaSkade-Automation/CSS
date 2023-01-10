# CSS-Ontology
An ontology for the Capability, Skill and Service model of Plattform Industrie 4.0

## Overview
This is an ontology implementation of the CSS reference model as defined by [this Plattform Industrie 4.0 Whitepaper](https://www.plattform-i40.de/IP/Redaktion/DE/Downloads/Publikation/CapabilitiesSkillsServices.html). The definitions according to this whitepaper can be found in a [Wiki page](https://github.com/hsu-aut/css-ontology/wiki/Definitions). The most important elements of this reference model are:

### Capability
A *Capability* is an implementation-independent specification of a function in industrial production to achieve an effect in the physical or virtual world. A *Capability* may be implemented by one or more *Skills*.
You can think of a capability as a machine-interpretable description of a function. Such a description typically features *Properties* and constraints on these properties.

### Skill
A *Skill* is an executable implementation of an encapsulated (automation) function specified by a *Capability*. Every *Skill* needs to have a *SkillInterface* (e.g. an OPC UA server) that allows external control of a *Skill*.

### Service
A *Service* is a description of the commercial aspects and means of provision of offered *Capabilities*. A service may be considered as a wrapper around a capability that adds additional information, typically when one wants to offer or request capabilities via a marketplace.


###

## Ontology example
:construction:Coming soon... :construction:

## Current Issues
Here are some known issues that were found while creating this ontology:
- There is an object property `offersUseOf`, which is used to connect a ServiceProvider with the Services it offers. In addition to `offersUseOf`, there is another object property `offers`, which connects a service with the capability it "embeds". This is a bit confusing. `offersUseOf` sounds like a sub property of `offers` but it is in fact something totally different.
The property `offers` should be changed, because a service doesn't "offer" anything actively. Maybe "contains" or "containsUseOf" would be better?

- `hasInput` and `isInputFor` sound like inverse object properties, but they are in fact totally different properties.
