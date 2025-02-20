---
layout: page
published: true
title: Best Practice
---

This is the best practice / style guide for the BBOP group. Inspired by / cribbed from [Knocean practice](https://github.com/knocean/practises/)

We are a diverse group working on many different projects with
different stakeholders and sets of collaborators. Nevertheless we
strive to follow a set of core best practices so we can be most
efficient and develop the highest quality code, ontologies, standards,
schemas, and analyses.

## Git and GitHub

- use git
- [commit early, commit often](https://deepsource.io/blog/git-best-practices)
   - perfect later!
   - you should always be working on a branch, so don't worry about breaking things
- Make repos public by default
- Use standard repo layouts
- Include standard files:
   - README.md
   - LICENSE (BSD3 preferred for software)
   - CONTRIBUTING.md
   - CODE_OF_CONDUCT.md (see for example [kgx CoC](https://github.com/biolink/biolink-model/blob/master/CODE_OF_CONDUCT.md)
   - Changes.md
   - .gitignore
   - Makefile or equivalent
- use GitHub
    - Like GitLab in principle, but GitHub has network effect
    - prefer to work on the main repo, not forks, but defer to project-specific guidelines
- use GitHub issues
    - in general you should always we working to a ticket assigned to you
    - try to assign every issue to somebody
    - try to have a single assignee / responsible person
    - tag people if necessary
       - note: if you tag me with @cmungall it's likely I won't see it. alert me to a ticket via slack if I am required
    - use GitHub's default labels: bug, question, enhancement, good first issue, etc.
    - set up standard issue templates (helps ensure tickets are auto-assigned)
- use GitHub Pull Requests
    - mark as draft until ready for review, then assign reviewers
    - description should link to an issue "Resolves #1234"
        - otherwise you have to clean up issues manually
    - update description as needed
    - always look over your PRs
        - are there unexpected changes? You should only see YOUR changes
        - Is it adding files unexpectedly? Some git clients are eager to do this
        - are some changes not recognizable as yours? **Be careful not to clobber**
        - follow repo-standard practice for rebase etc
    - AVOID:
       - making PRs too large
       - mixing orthogonal concerns in one PR. Generally 1PR = 1 issue
       - working on a PR for too long a time without feedback from others
       - working on "invisible" branches. ALWAYS make a PR, ALWAYS push. You can mark as draft!
- use GitHub Milestones to plan releases
- use GitHub Releases to tag versions and attach binaries
- use GitHub Pages for simple static content and documentation
    - prefer the `docs/` directory option
- use GitHub Projects ("project boards") for coordinating issues and PRs
    - three columns:
        - To do: for manager to fill and prioritize
        - In progress: for developer to keep up-to-date
        - Ready for review: for manager to empty
    - order of preference for cards: PR link, issue link, text
- set up GitHub actions to do CI
    - travis no longer recommended
    - use GitHub actions
- set up teams
    - default to public membership
    - make sure it is clear who has permission to merge PRs
- set up badges
- read our [GitHub Overview](https://docs.google.com/document/d/1YZ4kLyGka7MZPy824CHN7V2lnChFwJAGWpubKGr8n7w/edit)
- make sure all relevant artefacts are checked in
    - use `git status` and `.gitignore`
    - in general avoid checking in derived products (but see below)
    - avoid checking in .xslx files (use TSVs; or consider cogs instead)
- versioning
    - do not check in files with version numbers e.g. `foo.v1.txt` into GitHub - git does versioning for you
    - use the GitHub release mechanism
    - use ISO-8601 or semver schemes (see guidelines on specific repo types below)
- tend your repos
    - remove cruft such as obsolete files (GitHub preserves history)
    - avoid random stuff at top level
    - keep README in sync
    - avoid using spaces in filenames
    - always use standard suffixes (e.g. .tsv, .txt, .md)
    - kabob-case-is-a-good-default.txt
- use topics and star relevant repos
    - https://github.com/topics/linkml
    - https://github.com/topics/obofoundry
    - https://github.com/topics/geneontology

### Software-centric Repos

- Use an existing repo from a group member as template for best practice, e.g.,
   - [kgx](https://github.com/biolink/kgx/)
   - [linkml](https://github.com/linkml/linkml)
- Include a README.md
   - provide sufficient context
   - don't boil the ocean - put reference material in a separate reference guide
- Create reference documentation using RTD/Sphinx
   - let inline docstrings in Python do most of the work for you
- Include installation instructions
- use an OSI approved LICENSE, BSD3 preferred
- Use unit tests
   - consult others on framework
- Use GitHub-integrated CI
   - formerly Travis
   - use GitHub actions
- Release code to PyPI or appropriate repo
   - use GitHub releases
   - use GitHub actions to trigger releases to PyPI
      - use [GitHub actions to trigger releases to PyPI](https://packaging.python.org/guides/publishing-package-distribution-releases-using-github-actions-ci-cd-workflows/)
      - see [nmdc-schema](https://github.com/microbiomedata/nmdc-schema/tree/main/.github/workflows) as exemplar
- Consider a Dockerfile
- For ETL repos, follow standard templates for
   - kg-hub
   - koza
- For ETL repos
   - Use Jenkins pipelines
- Badges
   - CI
   - Code coverage
   - PyPI
   - TODO: ADD MORE

### Schema/Standards-centric Repos

- You will be using [linkml](https://github.com/linkml/linkml)
- Create repo from [LinkML template](https://github.com/link-modeling/linkml-template)
- Examples:
   - NMDC
   - MIxS
   - GFF3 linkml
   - [cmungall/chem-schema](https://github.com/cmungall/chem-schema)
- Register with w3id.org
- Include comprehensive examples
- Use LinkML mkdocs framework
- Understand the difference between [OWL-centric and KG-centric modeling](https://douroucouli.wordpress.com/2019/03/14/biological-knowledge-graph-modeling-design-patterns/)
- include mappings to biolink model
- always include examples
   - integrate these with documentation
   - integrate these with unit tests
- enable zenodo syncing

### Ontology-centric Repos

- Use [ODK seed](https://github.com/INCATools/ontology-development-kit/)
- Register ontology with OBO
   - include detailed metadata
   - include all products
   - include descriptive material in markdown
- Use GitHub for .owl distribution unless ontology is large, then consider:
   - GitHub releases
   - S3
- Follow group exemplars: Uberon, Mondo, GO, ENVO, CL, PATO
   - but be aware each has their quirks
- distribute useful products
   - distribute SSSOM
   - always distribute an .obo
   - always distribute a obo .json
   - distribute a kgx file (NEW)
   - distribute a rdftab sqlite file (NEW)
- use a sensible source format (foo-edit.owl)
   - .obo is best for diffs but less expressive and gotchas for CURIEs
   - functional syntax is often preferred
   - for template-based ontologies, much of the source may be TSVs
- enable zenodo syncing
- Understand issues relating to git conflicts with ontologies
   - .obo as source mitigates some of these
   - See [this thread](https://anatomy-and-cell-onto.slack.com/archives/C01A7LRAKN1/p1626433475018000?thread_ts=1626331368.016700&cid=C01A7LRAKN1)
   - See [this post](https://douroucouli.wordpress.com/2014/03/30/the-perils-of-managing-owl-in-a-version-control-system/)
      - many issues have since been resolved but unfortunately some remain

### Analysis/Paper-centric Repos

- One repo per paper
- Entire analysis must be reproducible via Makefile
   - All steps:
      - download
      - clean/pre-process
      - transform
      - training
      - evaluation
   - check with Chris before using snakemake/CWL/alternatives
   - Chris still uses biomake
- Use TSVs as default
- ALL TSVs MUST have data dictionaries
   - use LinkML (see above)
- check in small-mid size data files (<10m)
   - consider [cogs](https://github.com/ontodev/cogs) if TSVs must be managed in google sheets
- use JSON for complex data
- use KGX for anything that should be modeled as a KG
- use descriptive filenames
- manage metadata in GitHub
- sync repo with Zenodo
- use S3 for larger files
   - release files to Zenodo
- Dockerize   
- Use Jupyter notebooks
- Consider [Manubot](https://manubot.org/)
- Other recommended best practices
   - [datadryad](https://datadryad.org/stash/best_practices)
- enable zenodo syncing

## Websites

- GitHub pages favored over google sites over wikis
- Manage and author content as markdown, managed in github, with PRs as for code
- Google Analytics and similar (recommendations TODO)
- avoid manually authoring anything that can be derived from metadata
   - examplars: obofoundry.github.io, this site
- use a CC license, CC-0 or CC-BY


## Documentation

- all code, schemas, analyses, ontologies, MUST be documented
- code documentation is a love-letter to your future self
- understand [this four-way distinction](https://www.divio.com/blog/documentation/): tutorial, how-to, reference, explanation
- have strategies to avoid staleness and documentation being out of sync
- use inline documentation
    - publish via appropriate framework (RTD for code, mkdocs for schema, etc)
    - follow appropriate style guide
- examples, examples, examples
   - fenced examples in markdown docs
   - example standalone scripts
   - example Jupyter notebooks
   - unit tests can serve as examples
- use Markdown as default
   - RST acceptable for RTD
   - Google docs acceptable for initial brainstorming
   - Don't use Wikis (mediawiki, GitHub wiki)
   - Manage markdown docs as version control
   - publish as static site (RTD, mkdocs, etc)

## Coding/Python

- Python is the default language; use others as appropriate
   - javascript/typescript for client-side
       - don't implement domain/business logic in js. use python + APIs
   - Rust for speed
   - Scala for performance reasoners
   - Historically we used Java for anything requiring OWLAPI but being phased out
   - Chris still uses Prolog
- Why Python?
   - ubiquitous, cross-platform
   - good for scripting, interactive development
   - strong ecosystem of libraries for almost anything
   - Easy for developers to pick up
   - Most bioinformaticians know it
   - use for anything more than about 10 lines of Bash/Perl
   - use Python 3.6+
- Conform to the group style guide, or at least *some* style guide
   - [pep-0008](https://www.python.org/dev/peps/pep-0008/) for Python
   - use type annotations [PEP484](https://www.python.org/dev/peps/pep-0484/)
   - ReST or [numpy-style docstrings or google style](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/#type-annotations)
      - I think I favor ReST
   - See [knocean/practices/python](https://github.com/knocean/practises/tree/master/python)
      - I like the simplicity of venv, but we are also considering pipenv
      - Good advice: flake8, black, pytest
      - we use click not argparse [TODO: evaluate Typer]
      - Makefile defaults are good
      - Note unlike Knocean, we make use of OO as appropriate
- use flask/fastAPI for web apps
   - don't author OpenAPI directly; derive
- avoid authoring complex data models
   - use LinkML and derived datamodel classes
- use fstrings
- use typing
   - makes code more understandable
   - allows code completion in PyCharm etc
   - helps find bugs
- use dataclasses or pydantic
   - for DAOs, derive from linkml
- use an IDE
   - PyCharm is most popular
- ETL/ingest
   - follow existing exemplar repos
   - Read Chris' [10 simple rules for semantic ETL](https://docs.google.com/document/d/1Bgsyo-Z1oxEfxdNGB3KDM_NHfXYqdcXJIUd_j3iibi4/edit#)
- use requests for URL calls
- Always provide a CLI
   - separate CLI logic from core logic
   - Read [CLIG guidelines](https://clig.dev/)
   - Python: use click  [TODO: evaluate Typer]
   - design for composability
   - provide shortforms for common options
   - [Display help text when passed no options, the -h flag, or the --help flag](https://clig.dev/#help)
   - use de-facto standards
      - `-i`, `--input`
      - `-o`, `--output`
   - Follow exemplars
      - ROBOT
- Learning resources
   - [Charlie's Recommended Python Programming Videos](https://www.youtube.com/playlist?list=PLPFmTfhIBiumfYT3rsa35fHJxabB78er1)
- TODO: Best practice for
   - test framework (unittest vs pytest?)
   - environments: venv vs pipenv
   - config: requirements.txt vs toml vs Pipenv vs setup.cfg...
   - layout: src/name vs name
   - linter: black?

## Database Engines

- use whatever is appropriate for the job
   - blazegraph for ttl
   - neo4j for KGs
   - Postgresql for SQL db server
       - never use non-open SQL db solutions
       - Some legacy apps may use MySQL but Pg is preferred
   - sqlite for lightweight tabular
   - avoid vendor lock-in
       - use generic sparql 1.1 API vs triplestore specific APIs
   - solr for searchable / denormalized / analytics
      - always use golr patterns
      - read [semantic columnar store patterns](https://docs.google.com/document/d/1GoTZd4HSHI9q48Q6WUR4eDgBy0WgwsXcfVBihs_l0CU/edit)
- always have a schema no matter what the task
    - always derive from LinkML
- SQL vs other DB engines
   - this is an evolving area
   - see [Knocean SQL guide](https://github.com/knocean/practises/tree/master/sql)

## Handy developer and command line tools

- GNU Make -- see [Knocean guide](https://github.com/knocean/practises/tree/master/make)
- cogs
- odk
- [q](http://harelba.github.io/q/) -- query TSVs via SQL
- robot
- bash; small scripts only
- pandoc
- Docker
- editor of your choice

## Programming Libraries

- Data science
   - this is a fast changing field so recommendations here are general/loose
   - generally prefer Python >> R >> other languages for data sciences
   - we frequently use tensorflow, scikitlearn, keras
   - scikit-learn
   - catboost
   - pandas
       - TSV >> CSV
       - parquet for large files
       - use `#` for header comments
   - seaborn within Jupyter
   - KGs
      - [kgx](https://github.com/biolink/kgx)
      - [BMT](https://github.com/biolink/biolink-model-toolkit)
      - [EnsmallenGraph](https://github.com/AnacletoLAB/ensmallen_graph), (Rust + Python bindings), fast graph ML
      - [Embiggen](https://github.com/monarch-initiative/embiggen) graph ML (e.g. node2vec), and some other things like word2vec
      - [NEAT](https://github.com/Knowledge-Graph-Hub/NEAT) is a Python wrapper for reproducible graph ML in a YAML-driven way
      - also exploring pykeen ampligraph
- Ontologies
   - ontobio
   - OWLAPI (JVM) -- only where necessary
   - [obographviz](https://github.com/cmungall/obographviz/) (js)
   - beware of using rdflib and RDF-level libraries for working with OWL files, too low level
   - never, ever use XML parsers to parse RDF/XML
   - [Ubergraph](https://github.com/NCATS-Tangerine/ubergraph)
- NER/NLP
   - fast changing but some tools to consider:
      - runNER (which wraps OGER)
      - BERT for language models (experimental)
- Data
   - [curie_util](https://github.com/prefixcommons/curie-util)
   - LinkML
- Code
   - typing

## File formats, languages, and standards

- General
   - TSVs for columnar data
       - always have a data dictionary (use LinkML)
       - make it pandas-friendly
       - meaningful column names
       - SSSOM is an exemplar
       - understand [TidyData](https://vita.had.co.nz/papers/tidy-data.pdf) and Codd's [normal forms](https://en.wikipedia.org/wiki/Database_normalization#Normal_forms) and when to use them
   - hand-author YAML over JSON (+ follow schema)
   - Use JSON-LD / YAML-LD as appropriate
       - understand JSON-LD contexts
       - get context for free with LinkML
   - Turtle for some purposes
   - RDF/XML as default for OWL
- Ontologies
   - OWL
   - [OBO JSON](https://douroucouli.wordpress.com/2016/10/04/a-developer-friendly-json-exchange-format-for-ontologies/)
   - consider obo format deprecated. Exception: easier to maintain edit file as obo for git diff/PR purposes
   - COB as upper ontology, but also pay attention to biolink
   - Always use official PURLs for downloads
      - the OBO page gives the list of products. E.g. [obofoundry.org/ontology/pato](http://obofoundry.org/ontology/pato)
- Mappings (ontology or otherwise)
   - SSSOM with skos predicates
- KGs
   - biolink
   - kgx
   - RDF*
   - make available as:
      - RDF dump
      - Neo4J dump
      - sparql endpoint (consider putting into larger endpoint and segregating with NGs)
      - neo4j endpoint
      - KGX dump
      - KGX summary stats
- Schemas
   - everything must have a schema, including:
      - all TSVs should have data dictionary
      - JSON/YAML
      - KGs
      - OWL ontologies and OWL instance graphs
   - Understand basic concepts:
      - normalized vs de-normalized
      - identifiers and URIs
      - closed-world vs open-world
      - schema vs ontology
   - Always author schemas in linkml
      - derive alternate representations (e.g. json-schema)
   - JSON-schema for JSON-centric projects (never author, always derive from LinkML)
   - ShEx for ontology-centric (try and derive from LinkML)
   - kwalify is deprecated for us
   - Always have a LinkML schema even when using
      - python dicts
      - open-ended JSON/YAML
      - RDF
      - Neo4J
      - ad-hoc TSVs
   - Include mappings:
      - map to biolink
- Versioning
   - Semantic Versioning (semver) by default
   - ISO-8601 OBO style for ontologies
   - use GitHub releases for versioning as appropriate
   - release versions to appropriate repository/archive
- Text
   - markdown by default
      - frontmatter metadata where appropriate
      - track in version control
- APIs
   - RESTfulness
      - true REST may be too high a barrier
      - RPC-style (i.e. swagger/openAPI) may be fine
   - All web APIs should have OpenAPI exploration interface
   - derive OpenAPI from Python code
      - flask or fastapi
   - Must have Docker container
   - Use grlc to make APIs from sparql endpoints

- CURIEs and IRIs
   - Read [McMurry et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5490878/pdf/pbio.2001414.pdf)
   - always use CURIEs for IDs
   - always use registered prefixes
   - understand at a broad level the different registries:
       - http://identifiers.org
       - http://n2t.net -- synced(?) with identifiers.org but broader context
       - http://bioregistry.io/
          - has a lot of advantages over id.org: more transparent, github metadata based, lightweight
       - https://github.com/prefixcommons/biocontext
          - we developed this as an "overlay" on existing registries
   - have an explicit JSON-LD context or prefixes yaml file
   - Use the [prefixcommons curie util library](https://github.com/prefixcommons)
   - Read the identifiers guides closely, even for projects you are not on
      - [Translator SRI/biolink identifiers](https://biolink.github.io/biolink-model/#identifiers)
      - [Identifiers in NMDC](https://microbiomedata.github.io/nmdc-metadata/identifiers/)
      - [Identifiers in GO](http://wiki.geneontology.org/index.php/Identifiers)
      
- Genomics
   - GFF3
   - SO
- Annotation
   - GAF
   - GPAD
   - Phenopackets
- Dates
   - If you don't use ISO-8601 you will go to hell

## Portability

- it should be easy for anyone to install from any of our repos
- everything should run on macos or linux
- provide a Docker image for anything complex
- use standard installation idioms

## Key specialized libraries and command line tools

- [ontobio](https://github.com/biolink/ontobio), for ontologies and associations
- [kgx](https://github.com/biolink/kgx)
- [ODK](https://github.com/INCATools/ontology-development-kit) and [ROBOT](https://github.com/ontodev/robot), for ontologies
- runNER for NER

## Building Ontologies

- ontologies are for users, not ontologists
  - OWL and description logic is necessary for building robust ontologies, but needn't be exposed
  - Minimize philosophy
  - avoid unnecessary abstractions
- ontologies should have annotations
   - annotations, as in the sense used by curators
   - ontologies without annotations are generally of limited use, avoid working on them
- learn tools and best practice for robust ontology engineering
  - Read [my Onto-Tips](https://douroucouli.wordpress.com/2019/03/09/ontotips-a-series-of-assorted-ontology-development-guidelines/)
  - Use [ODK](https://github.com/INCATools/ontology-development-kit)
  - Use [ROBOT](https://github.com/ontodev/robot)
  - Do the GO OWL tutorial
  - For advanced OWL-centric tasks, use scowl
- use the ontologies we work on as examplars
   - GO
   - Mondo
   - Phenotype Ontologies
   - ENVO
   - Uberon
   - RO
- follow OBO best practice and principles
   - ontologies should be open
   - if OBO is underspecified, follow the examples of projects done in this group
      - oio over IAO
      - liberal axiom annotations
      - key annotation properties: synonyms, definitions, mappings
      - See [documentation on uberon synonyms](https://github.com/obophenotype/uberon/wiki/Using-uberon-for-text-mining), this is an exemplar for us
      - dosdp over robot, but always use the more appropriate tool for the job
- include comprehensive definitions clear to biologists
   - [read my definitions guide](https://douroucouli.wordpress.com/2019/07/08/ontotip-write-simple-concise-clear-operational-textual-definitions/)
- understand [compositional patterns](https://douroucouli.wordpress.com/2019/06/29/ontotip-learn-the-rector-normalization-technique/)
- avoid overmodeling
- Document ontologies
   - [document design decisions](https://douroucouli.wordpress.com/2019/06/16/ontotip-clearly-document-your-design-decisions/)
   - write clear operational definitions
   - document your design patterns
      - Watch [design pattern presentation](https://douroucouli.wordpress.com/2020/11/02/aligning-design-patterns-across-multiple-ontologies-in-the-life-sciences/)
      - Mondo is our exemplar
- understand limitations
- use ontologies only where appropriate
   - vocabularies
   - descriptors
   - don't use an ontology where a schema is more appropriate
   - don't use an ontology where a KG is more appropriate. See [KG vs ontology DPs](https://douroucouli.wordpress.com/2019/03/14/biological-knowledge-graph-modeling-design-patterns/)
- make best effort attempt to provide mappings
   - use SSSOM
   - use boomer

## Collaboration

- we are a collaborative group, reach out if you have issues
   - join relevant channels on bbop and other slacks
   - questions always welcome but make best effort to see if information available in group reference guides
- make things easier for those who follow you
   - the same questions often come up repeatedly
   - if someone answers a question for you, update the relevant guide to make it clearer for others
- follow codes of conduct
- be constructive in any criticism
- use your Berkeley Lab account for email, calendars
- keep your calendar up to date, this facilitates scheduling meetings
- slack
   - avoid `@channel` unless necessary
   - don't be a channel anarchist
   - discussion about tickets OK but decisions and key points must be recorded in ticket
- use GitHub for requests
- Use GitHub for requesting terms from ontologies etc
   - [Data mapping guide: selecting and requesting terms from ontologies, data models, and standards](https://douroucouli.wordpress.com/2021/07/03/how-select-and-request-terms-from-ontologies/)

## Google docs/slides/sheets hygiene

- Use google docs/slides over Microsoft/Apple/Desktop
    - but sometimes markdown+git is more appropriate than either
    - for grants, papers, and other collaborative documents, move to Word at last possible minute (if at all)
    - pandocs can be used to make markdown
    - avoid latex/beamer unless it is really called for
- Use tagging/comments/modes appropriately
    - If it's not your doc, default to Suggesting mode
       - use your judgment; minor direct edits to correct typos usually OK
       - respect conventions of document owner
    - use comment feature to make comments, don't write your comment in a different color
    - avoid use of text color as semantics
    - assign/tag people appropriately
    - avoid comment wars
- Make the doc outline-mode-friendly
    - use H1/H2/etc
    - always have outline mode on (list-like icon near top left)
    - assume the reader has outline mode on
    - rarely need for a TOC
- For google sheets / excel
    - never manually color code or use font/strikethrough. Always add an explicit field and use conditional formatting
    - always have a schema, even if it is a flat data dictionary. linkml-model-enrichment will derived one
- Use formatted templates where appropriate (grants, papers)
- Use Paperpile for citations / reference management (you have access via the lab)
- Give documents meaningful names (e.g., not just "meeting")--assume that most people will find the doc via search rather than by going through the folder hierarchy
- Use a rolling agenda/notes doc, rather than one doc per meeting
- always have a google doc for every meeting you are in
- include a link to the rolling doc in calendar invites
- include the Zoom / videoconference link in the rolling notes doc
- organize google docs in the relevant folder depending on what project is funding the work
- understand how navigation works for google docs
- make visible to all by default
- include links to slides of general relevance from project repos
- favour TSV+github over google sheets
   - workflows clearly favor sheets
   - when using sheets, use [cogs](https://github.com/ontodev/cogs)
- follow TSV guidelines for google sheets
- don't use color for semantics. Always use conditional formatting for colors etc
- reuse slides from existing slide decks, but provide attribution

## General Principles

- DRY: Don't Repeat Yourself
   - but avoid over-abstraction and frameworkitis
- various 10 simple guides:
   - [10 simple rules of quick and dirty scientific programming](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1008549)
- Always reuse
   - we probably have a Python library for it
   - reuse general design patterns
   - GitHub templates
   - follow exemplar repos
       - [kgx](https://github.com/biolink/kgx) and [linkml](https://github.com/linkml/linkml) for general python
       - [kg-covid-19](https://github.com/Knowledge-Graph-Hub/kg-covid-19) for ETL
   - try especially hard not to reinvent what someone in the group or our collaborator has done
- Avoid perfectionism
   - iterate on solutions
   - smaller batches of incremental progress >> long delays on perfect solution (that may turn out to be flawed)
- For many tasks, the 80/20 rule may suffice
   - Don't boil the ocean
   - beware of rabbit holes
- More to come...
