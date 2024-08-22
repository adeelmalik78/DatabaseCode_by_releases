# Database Code By Release Directories

This repository demonstrates how to organize database scripts in directories organized by releases.

## Directory Structure
Here is the high-level overview of the directory structure. Note that there is a directory for each release (`1.0`, `1.1`, `2.0` and so on). 
```
.
├── README.md
├── liquibase.properties
└── sqlcode
    ├── 1.0
    ├── 1.1
    ├── 2.0
    ├── 2.1
    ├── 2.2
    ├── 3.0
    └── rootchangelog.xml
```

Here is the entire directory structure of this repo. There are schema subdirectories in each release directory. And each schema subdirectory has its own changelog file (e.g., `schema1changelog.xml`). 
```
.
├── README.md
├── liquibase.properties
└── sqlcode
    ├── 1.0
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    ├── 1.1
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    ├── 2.0
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    ├── 2.1
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    ├── 2.2
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    ├── 3.0
    │   ├── changelog.xml
    │   ├── schema1
    │   │   └── changelog.xml
    │   ├── schema2
    │   │   └── changelog.xml
    │   └── schema3
    │       └── changelog.xml
    └── rootchangelog.xml
```



## Changelog files
Note that there is a [rootchangelog.xml](sqlcode/rootchangelog.xml) which serves as the entry point changelog for Liquibase (as specified in [liquibase.properties](liquibase.properties) file). This file points to `changelog.xml` file in each release directory:
```xml
  <include file="1.0/changelog.xml" relativeToChangelogFile="true"/>
  <include file="1.1/changelog.xml" relativeToChangelogFile="true"/>
  <include file="2.0/changelog.xml" relativeToChangelogFile="true"/>
  <include file="2.1/changelog.xml" relativeToChangelogFile="true"/>
  <include file="2.2/changelog.xml" relativeToChangelogFile="true"/>
  <include file="3.0/changelog.xml" relativeToChangelogFile="true"/>
```

`changelog.xml` file in each release directory points to a changelog.xml file in each schema directory:
```xml
  <include file="schema1/changelog.xml" relativeToChangelogFile="true"/>
  <include file="schema2/changelog.xml" relativeToChangelogFile="true"/>
  <include file="schema3/changelog.xml" relativeToChangelogFile="true"/>
```

