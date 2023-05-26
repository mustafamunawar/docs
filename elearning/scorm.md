# SCORM: Shareable Content Object Reference Model

- SCORM is a technical specification for eLearning software products. It standardizes the way in which eLearning courses are created, and how they’re launched.

- SCORM (Shareable Content Reference Model) is a technical specification for eLearning or online training material. It is the format in which training content should be downloaded or exported for uploading to a SCORM-compliant learning management system (LMS). Training content published in SCORM ensures that your LMS recognizes its data model and can functionally work together without issues.

- In short SCORM can be described as two things: `packaging content` and `exchanging data at Run-Time`.

- `Packaging content` or the `content aggregation model (CAM)` determines how a piece of content should be delivered in a physical sense. At the core of SCORM packaging is a document titled the `imsmanifest`. This file contains every piece of information required by the LMS to import and launch content without human intervention. This manifest file contains `XML that describes the structure of a course both from a learner’s perspective and from a physical file system perspective`. Questions like, “Which document should be launched?” and “What is the name of this content?” are answered by this document.

- `Run-Time communication, or data exchange`, specifies `how the content ”talks” to the LMS while the content is actually playing`. This is the part of the equation we describe as `delivery and tracking`. There are two major components to this communication. First, the content has to “find” the LMS. Once the content has found it, it can then communicate through a series of “get” and “set” calls and an associated vocabulary. Conceptually, these are things like `request the learner’s name` and `tell the LMS that the learner scored 95% on this test` Based on the available SCORM vocabulary, many rich interactive experiences can be communicated to the LMS.

- A `SCORM package` also referred to as a `SCORM module`, `SCORM course` or `SCORM file` , is a ZIP file exported via SCORM format. This file is also called a `Package Interchange File (PIF)` by some learning lectures or platforms.

- SCORM works via its two main components; Sharable Content Object (SCO) and Reference Model(RM). SCO is focused on making the contents in your SCORM package shareable. This helps to ensure that anything exported in SCORM (format?) can be shared across various content authoring tools or learning management systems.

- A Sharable Content Object (SCO) is the most granular piece of training in a SCORM world. Some would call it a `module`, a `chapter`, a `page`… the point is that it varies wildly. A SCORM purist would tell you that it should be the smallest piece of content that is both `reusable` and `independent`. In terms of how the LMS treats it, this is the item `shown separately in the table of contents` and `tracked separately from other items`. It `can contain its own bookmark, score and completion status`.

- Reference Model (RM) is a well-known industry standard used throughout the eLearning industry. In other words, it's what most LMS are programmed to accept.

- The RM also holds the run-time communication or data exchange. This allows the SCORM package to "talk" or communicate with your selected LMS so that it follows the rules or instructions given. For example, you can decide in which order your learning content should be distributed and/or request test scores for specific trainees for tests placed in the LMS to track learning-related activity.

- Simply put, SCORM allows you to share, communicate details and track your training content with an LMS.

- `SCORM 1.1`
  The first version was introduced in January 2001.

- `SCORM 1.2`
  The second version was introduced in October 2001 and is still the most widely used today.

- `SCORM 2004`
  The third version was introduced January 2004 but later updated. The most recent edition is SCORM 2004 (4th edition), which was introduced in March 2009.

- `Experience API` (`Tin Can` or xAPI)
  Experience API was introduced in April 2013 as a way of expanding SCORM capabilities. The basis is very similar; however, xAPI gives developers the ability to share, read, and write data with a data store, also known as a `learning record store (LRS)`.

- The much more up-to-date alternative, `xAPI (Experience API)`, also called `Tin Can`, is slowly becoming the new industry standard and favorite. Online corporate training has changed significantly since 2004, and xAPI has a few more features that match the needs of current training and development professionals or content authors.

- Specifications of SCORM

  SCORM is composed into three categories–all of which must be met in order for content to be considered SCORM compliant. These categories include Content Packaging, Run-Time, and Sequencing.

1. `Content Packaging`

   - Content must be packaged into a self-contained directory or archive file format known as a ZIP.

   - Within this ZIP there must be an `XML file named imsmanifest.xml` (the `manifest file`). Within the manifest, the course must be divided into one or more parts called an `SCO (Shareable Content Object)`. In Lectora/Lectora Online, the SCO is also known as an Assignable Unit (AU).

2. `Run-Time Communication`
   Content publishing to an LMS must be `web deliverable and launched in a web browser (new window or frameset)`. Only one SCO may be launched at a time. Once the content has been launched it must communicate between the eLearning and LMS using JavaScript. `Run-Time` is responsible for data exchange between an LMS and the content and deals with what is called `delivery and tracking`. First, the content “finds” the LMS and then they communicate through “get” and “set” calls and a corresponding vocabulary. Simply put, these are things like `ask the learner’s name` and `inform the LMS that the learner scored 80% on this quiz` etc.

3. `Sequencing`
   In general, sequencing determines navigation and performance. It can determine the navigation provided, specify prerequisites that are required, give you the ability to use weighted questions or question pools, and offer options for remediation. In other words `Sequencing` relates to how a learner navigates through the course. For example, it directs how a user moves after performing certain actions like hitting the next button and defines which activities have to be completed before they go to the next step.

## Files that a SCORM package contains

Following are the contents every SCORM package should include:

- XML (eXtensible Markup Language) manifest file (imsmanifest.xml). The manifest file describes the package and its contents. The mandatory data it should contain are the unique identifier, the minimal metadata describing the package and its SCORM version, resource definitions that list all files necessary to launch and deliver each resource, and organization of learning activities.

- Resource files used by the content package (“parts” that make up the course) and its learning activities.

-Schema/definition XSD (XML Schema Definition) and DTD (Document Type Definition) files that refer to the manifest file.

## How does SCORM relate to AICC, xAPI and cmi5?

- SCORM is a reference model, which means that it is built on top of existing specifications. From the beginning, SCORM has been described as a “best of breed” solution, culling the best pieces of prior specifications.

- AICC, a standard from the aviation industry, was used as a basis for the Run-Time communication portion of the SCORM specification. Conforming to one standard does not mean that you automatically conform to the other.

- xAPI, also referred to as the Experience API or Tin Can API, is often considered the “next generation of SCORM” and is newest eLearning standard. At Rustici Software, we worked closely with ADL on Project Tin Can (the beginnings of xAPI), imparting our decade of SCORM knowledge to make sure that xAPI is a huge leap forward for the eLearning community. xAPI is vastly different than SCORM and provides a more flexible way to track a wide variety of learning, including activities that occur outside of the LMS.

- cmi5 is an xAPI profile used when xAPI activities are launched from an LMS. cmi5 defines the necessary components for system interoperability such as packaging, launch, credential handshake and consistent information model.

## Representing SCORM Content

The heart of the SCORM content packaging specification is the course’s manifest file. The manifest is an XML file that completely describes the content. It contains several essential pieces:

### Resources

Resources are a list of “parts” that make up the course. There are two types of resources, SCOs and Assets.

An Asset is a collection of one or more files that makes up a logical unit. Assets can either be stand alone units of instruction (“parts” of the course), or they can be logical collections of files that are reused in other parts of the course (a common set of branding images for instance).
SCOs are units of instruction that are also composed of one or more files. SCOs are almost always instructional parts of a course.

The key difference between a SCO and an Asset is that `a SCO can communicate with the LMS`, whereas `an Asset is simply static content` that is presented to the user/student/learner. Any resource that can be launched by the learner/student contains a pointer to the page to which the LMS should redirect the learner in order to launch the resource. Resources should also contain a comprehensive list of all the files required for proper functionality of the resource so that they can be ported to new environments and still continue to function.

### Organizations

`Organizations` are logical groupings of the parts of a course (resources) into a hierarchical structure. A single manifest can contain more than one organization of the same content (for instance, to enable the content to be presented differently to different audiences), but `typically there is just a single organization`, the default organization. Organizations are always structured hierarchically, as a tree. The nodes within this tree are known as “activities” (when referencing them in the context of sequencing) or “items” (when referencing them in the context of content packaging). Any item can have child items nested beneath it. When an item has children, it is referred to as an “aggregation” or “cluster”. Items that do not have any children are required to reference a resource. This resource is what is delivered to the learner when the item is selected. Items that do have children are not allowed to reference resources, they are purely containers for other items. (This can be thought of like the file structure found on a computer… items are either a folder or a file, but not both. Folders may contain other folders or files, but “empty folders” are not permissible.)

### Metadata

Every piece of the manifest can be described in detail by associating metadata with it. SCORM metadata is recorded in a well-defined format known as “learning object metadata”, or “LOM”. LOM contains many predefined fields for describing learning content. SCORM also permits the extension of LOM to allow organizations to specify additional metadata. Metadata can be applied to virtually any section of the manifest, for instance it can be applied to the course as a whole, to individual items, or even to individual resources and files to enhance their reusability. Within the manifest file, metadata can either be specified inline within the XML (recommended for small amounts of metadata, especially at the course level), or it can be specified by linking to an external metadata file (recommended for large amounts of detailed metadata). Metadata is typically optional, however SCORM 1.2 does place some restrictions on the minimal subset of data that must be specified if any data is specified. The appropriate amount of SCORM metadata to use will vary widely depending on the intended use of the content, its anticipated longevity, and likelihood that the content will be reused.

### Sequencing

In SCORM 2004, every activity can have a set of sequencing rules assigned to it. These rules are encoded in XML in the course manifest. SCORM was designed so that a simple course consisting of nothing but assets should not need to specify any sequencing rules except for the defaults. However, in practice, there are some defaults that should be overridden for all but the simplest of courses.

### Packaging the Content

Once the content has been represented in XML, it is saved into a file called “imsmanifest.xml”. The manifest file must always exist at the root of the content. To be fully conformant, the content should also include a set of XML schema definition files (.xsd and .dtd files) that formally describe the XML grammar contained within the manifest, including any extensions that may have been used. (Download the SCORM manifest schema definition files). Content can then be delivered either in a simple directory (for instance on a CD), or it can be placed in a ZIP file. When content is put in a ZIP file, it is known as a “package interchange file” or “PIF”. PIFs are far and away the most common SCORM delivery format.

An important principle of content packaging is that ideally, everything needed to deliver the course should be self-contained within the PIF file. SCORM strongly encourages portability and reuse. To maximize these goals, every file needed to deliver the course should be contained within the PIF and listed in the manifest. Furthermore, content developers should avoid the use of server-side code and other dependencies like databases. The use of these tools, as well as external dependencies, is allowed by SCORM, however the industry norm is to avoid them when possible.
