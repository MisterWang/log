---
title: libxml2的树结构
categories: 
- c
- libxml2
tags:
- libxml2
layout: post
---
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

## xmlNode
xml树结构为:
```
0 
|\\\
| \\ \ 
0-0-0-0
|\   /|
0-0 0-0
      |\
      0-0
```
每个节点有两个指针分别指向子节点链表的头和尾，另外有两个指针分别指向当前兄弟链表的前驱节点和后驱节点,以及一个父节点指针。

```c
struct _xmlNode {
    void           *_private;	/* application data */
    xmlElementType   type;	/* type number, must be second ! */
    const xmlChar   *name;      /* the name of the node, or the entity */
    struct _xmlNode *children;	/* parent->childs link */
    struct _xmlNode *last;	/* last child link */
    struct _xmlNode *parent;	/* child->parent link */
    struct _xmlNode *next;	/* next sibling link  */
    struct _xmlNode *prev;	/* previous sibling link  */
    struct _xmlDoc  *doc;	/* the containing document */

    /* End of common part */
    xmlNs           *ns;        /* pointer to the associated namespace */
    xmlChar         *content;   /* the content */
    struct _xmlAttr *properties;/* properties list */
    xmlNs           *nsDef;     /* namespace definitions on this node */
    void            *psvi;	/* for type/PSVI informations */
    unsigned short   line;	/* line number */
    unsigned short   extra;	/* extra data for XPath/XSLT */
};
```

## xmlDoc
document结构保存了一份id的映射表用来通过id快速找到节点。
```c
struct _xmlDoc {
    void           *_private;	/* application data */
    xmlElementType  type;       /* XML_DOCUMENT_NODE, must be second ! */
    char           *name;	/* name/filename/URI of the document */
    struct _xmlNode *children;	/* the document tree */
    struct _xmlNode *last;	/* last child link */
    struct _xmlNode *parent;	/* child->parent link */
    struct _xmlNode *next;	/* next sibling link  */
    struct _xmlNode *prev;	/* previous sibling link  */
    struct _xmlDoc  *doc;	/* autoreference to itself */

    /* End of common part */
    int             compression;/* level of zlib compression */
    int             standalone; /* standalone document (no external refs)
				     1 if standalone="yes"
				     0 if standalone="no"
				    -1 if there is no XML declaration
				    -2 if there is an XML declaration, but no
					standalone attribute was specified */
    struct _xmlDtd  *intSubset;	/* the document internal subset */
    struct _xmlDtd  *extSubset;	/* the document external subset */
    struct _xmlNs   *oldNs;	/* Global namespace, the old way */
    const xmlChar  *version;	/* the XML version string */
    const xmlChar  *encoding;   /* external initial encoding, if any */
    void           *ids;        /* Hash table for ID attributes if any */
    void           *refs;       /* Hash table for IDREFs attributes if any */
    const xmlChar  *URL;	/* The URI for that document */
    int             charset;    /* encoding of the in-memory content
				   actually an xmlCharEncoding */
    struct _xmlDict *dict;      /* dict used to allocate names or NULL */
    void           *psvi;	/* for type/PSVI informations */
    int             parseFlags;	/* set of xmlParserOption used to parse the
				   document */
    int             properties;	/* set of xmlDocProperties for this document
				   set at the end of parsing */
};
```
