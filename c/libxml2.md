# libxml2

## xmlEntity
```c
struct _xmlEntity {
    void           *_private;	        /* application data */
    xmlElementType          type;       /* XML_ENTITY_DECL, must be second ! */
    const xmlChar          *name;	/* Entity name */
    struct _xmlNode    *children;	/* First child link */
    struct _xmlNode        *last;	/* Last child link */
    struct _xmlDtd       *parent;	/* -> DTD */
    struct _xmlNode        *next;	/* next sibling link  */
    struct _xmlNode        *prev;	/* previous sibling link  */
    struct _xmlDoc          *doc;       /* the containing document */

    xmlChar                *orig;	/* content without ref substitution */
    xmlChar             *content;	/* content or ndata if unparsed */
    int                   length;	/* the content length */
    xmlEntityType          etype;	/* The entity type */
    const xmlChar    *ExternalID;	/* External identifier for PUBLIC */
    const xmlChar      *SystemID;	/* URI for a SYSTEM or PUBLIC Entity */

    struct _xmlEntity     *nexte;	/* unused */
    const xmlChar           *URI;	/* the full URI as computed */
    int                    owner;	/* does the entity own the childrens */
    int			 checked;	/* was the entity content checked */
					/* this is also used to count entities
					 * references done from that entity
					 * and if it contains '<' */
};
```
