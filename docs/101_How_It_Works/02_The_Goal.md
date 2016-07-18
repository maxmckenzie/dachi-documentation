Our goals for Dachi are fairly simple, we created Dachi to fulfill our needs in web development. Our needs required us
to seek a system with maximum performance and flexibility. We needed a system that could scale well and handle many
request with little overhead. We have experimented with many technologies, over many years in production and we feel the
current revision of Dachi achieves all of our goals at the moment.

To achieve our goals we constantly strive to inspect every aspect of the framework and attempt to further reduce
complexity and increase performance. Anything that doesn't match out goals, doesn't make it into the framework.

### Key Concepts
**Librarification** Any code that can be converted into a library, should be converted into a library. This aids
future development by allowing code re-use. This also promotes seperation between components.

**Be Dynamic** Load only what you need, request only what you require, supply only what is requested. This concept is
relevent from the core (only required framework logic should be loaded, only only when required) to the user (modules
should only supply the relevent data and not the whole objects).

**Don't Reinvent** We currently use Composer as our package management system. This provides us with a massive 
selection of third-party open-source libraries and tools. Where something has already been made, and performs
sufficently, you should thank the existing developer and implement it.

**Test It** All of the Dachi core code has complete test coverage over every feature. We strive to update these tests
with changes and continue to create new tests for new functionality. Libraries with tests should be prefered over those
without.