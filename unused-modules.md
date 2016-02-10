---
layout: default
title: Unused Modules and Component Dependencies
---

When the Dagger processor generates components, it only requires instances of
modules and component dependencies that are explicitly needed to supply requests
for a binding.

*   If all of a module's methods that are used in the component are static,
    Dagger does not need an instance of that module at all. Dagger can invoke
    the static methods directly without a module.
*   If a module provides no bindings for a Component, no instance of that module
    is necessary to construct the graph.
