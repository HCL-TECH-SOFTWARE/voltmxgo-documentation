# Apache CouchDB Adapter

The Apache CouchDB[^1] adapter in Volt Foundry is a business adapter that facilitates seamless integration between Volt Foundry applications and Apache CouchDB databases. It utilizes CouchDB's native RESTful HTTP/HTTPS API to perform essential data operations within CouchDB. This adapter enables Volt MX applications to efficiently connect to CouchDB back-end data, supporting standard CRUD operations and queries through CouchDB views. By leveraging the native REST API, the adapter ensures robust and reliable communication with CouchDB databases.

[^1]:Apache CouchDB and CouchDB are trademarks of The Apache Software Foundation.

## OData filter support

The CouchDB adapter supports basic OData composite filters along with support for select fields. These apply to the GET method.

Basic OData composite filters are filter expressions that combine multiple filter conditions using logical operators, such as `and` and `or`, and grouping by parentheses to refine query results. These filters operate on resource properties using comparison operators, such as `eq` or equals and `ne` or not equals.

!!! warning "Important"

    CouchDB does not natively support OData filters, so the Apache CouchDB adapter retrieves records from CouchDB and applies the OData filters to these records. This approach may introduce performance overhead when processing large numbers of documents. It is recommended to thoroughly test your use cases to identify and mitigate any potential performance issues.

**Examples**

- `country eq 'India' or country eq 'China' or country eq 'Singapore'`
- `(country eq 'India' and name eq 'Chennai') or country eq 'China' or country eq 'Singapore'`
- `country eq 'India' or (country eq 'China' and name eq 'Shanghai') or country eq 'Singapore'`
- `(country eq 'India' and name ne 'Chennai') or (country eq 'China' and name eq 'Shanghai') or country eq 'Singapore'`
- `((country eq 'India' and name ne 'Chennai') or (country eq 'China' and name eq 'Shanghai'))`
- `(country eq 'India' and population eq 50000) or (country eq 'China' and population ge 10000)`
- `(country eq 'India' and population eq 50000) or (country eq 'China' and population ge 100)`
- `(continent eq 'AS' or continent eq 'NA') and (population ge 50000)`
- `(continent eq 'EU' or continent eq 'NA') and (population le 50000)`
- `(continent eq 'EU' and population ge 10000 and censusdate gt '2022-10-15')`
- `(continent eq 'EU' and population ge 10000 and censusdate gt '2024-10-15')`
- `(continent eq 'EU' and population ge 10000) and (censusdate ge '2023-01-01' and censusdate le '2023-12-31')`

## Schema management

Although CouchDB is schema-less, in most use cases, the documents stored in them invariably have some schema with integrity enforced via applications that consume the data.

The Apache CouchDB adapter infers the schema based on the first document returned in a view and displays this inferred schema in the configuration tab for user confirmation. Using the first document for schema inference is a deliberate design choice aimed at simplifying maintenance and improving efficiency. This inferred schema enhances the developer experience by enabling richer OData filtering capabilities.

Additionally, the adapter provides an API endpoint that enables developers to query and modify the first document in a view to keep the inferred schema up to date. Common scenarios for this include:

- Introducing new fields in newer documents, which are absent in older documents and impractical to retroactively add.
- Removing obsolete fields that are no longer relevant.

For more information on importing the API endpoint, see [Import ViewSchema endpoint into Apache CouchDB data model](../howto/couchdb/imprtschema.md).

For more information on how to keep the inferred schema current, see [Query and update the first document in a CouchDB view for schema management](../howto/couchdb/viewupdate.md).
