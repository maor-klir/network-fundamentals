# Deliverables

## Link to SR Linux documentation page

1. https://containerlab.dev/manual/kinds/srl/#user-defined-startup-config
2. https://containerlab.dev/manual/kinds/srl/#license

## Link to an interesting community lab repo with brief description

- https://github.com/metal-stack/mini-lab:
  A small, virtual setup to locally run metal-stack.  
  It deploys the metal control plane and a metal-stack partition with two simulated leaf switches.  
  The lab can be used for trying out metal-stack, demonstration purposes or development.
- What ius metal-stack?
  metal-stack is a set of microservices implementing Metal as a Service (MaaS), turning a bunch of hardware into elastic cloud infrastructure.   
  It is built to manage the lifecycles for hundreds and thousands of servers inside your on-premises data center.

## One observation from the Discord community

Nokia has no official Ansible playbooks for SR Linux (Service Router Linux) / NVD (Nokia Validated Designs):  
Community repo `srl-labs/intent-based-ansible-lab` (https://github.com/srl-labs/intent-based-ansible-lab) is the de facto reference.  
Nokia's preferred automation path is EDA (Event-Driven Automation).
