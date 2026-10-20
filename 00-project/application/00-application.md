# Design and Implementation of an Inventory Tracking and Logistics Management Platform

## My interpretation of the brief

I understand this project as designing and implementing a multi-user web application for centrally managing inventory across multiple warehouses.

The system should use a relational database to represent products, hierarchical categories, warehouses, stock balances, stock movements, and user access. Users should be able to inspect inventory for individual products and aggregate it across categories and their subcategories.

The main challenge is maintaining correct inventory when several users perform operations at the same time. For example, transferring ten units between warehouses must decrease the source balance and increase the destination balance together. If either operation fails, the entire transfer should be rolled back. Concurrent operations must not allow stock to be deducted twice or become negative.

The application should also provide an administrative dashboard with alerts and statistics, combined filters, PDF inventory lists, authentication, and role-based access for administrators and warehouse staff. Automated tests and preparation for installation in a server environment are integral parts of the project.

## Why I am a good fit for this project

I am interested in how everyday inventory operations can be translated into clear business rules and a reliable database design.

What interests me most is how a system can keep a consistent view of stock across different warehouses while several people use it simultaneously. A transfer looks simple in the interface, but it requires careful coordination of validation, permissions, and database updates.

I would like to understand how relational database design, transaction management, and automated testing work together to make a practical web application dependable. I am also interested in presenting complex inventory information through useful filters, alerts, and reports.

## Relevant experience and background

I would like to develop my skills in web application development, relational database modelling, authentication, and automated testing through this project.

My approach would be to implement a small end-to-end workflow first, verify its behaviour, and then extend it systematically. I would agree the final technology stack and deployment requirements with the supervisor.

## Proposed approach

I would begin by documenting the main workflows: creating products and categories, receiving and issuing stock, transferring stock between warehouses, reviewing balances, and generating reports.

The database would separate product information from per-warehouse stock balances and retain a stock-movement history. Foreign keys, uniqueness rules, and appropriate quantity constraints would support integrity. Category relationships would form a hierarchy without cycles. Category totals would include descendant categories without double-counting products, and quantities would only be aggregated where their units are compatible.

Transfers would execute in a single database transaction. A concurrency-control strategy, such as row locking or conditional balance updates, would prevent simultaneous requests from spending the same stock. Repeated submissions should not create duplicate transfers. The balance updates and corresponding movement records would commit or roll back together.

Authentication and authorisation would be enforced on the server. Administrators would manage configuration and users; warehouse staff would receive only the operations and warehouse access permitted by the agreed role model.

The dashboard would present clearly defined statistics and alerts, initially including stock below configured thresholds. Combined filters could cover warehouse, category and descendants, product, and stock status. PDF inventory lists would reflect the selected filters and identify their generation time.

Automated integration tests would verify successful transfers, insufficient-stock rejection, rollback after failure, concurrent updates, duplicate requests, access restrictions, and consistency between balances and movement history. Additional checks would cover hierarchical totals, filters, and PDF report contents.

Server installation preparation would include database migrations, configuration through environment variables, dependency installation, startup instructions, and documented backup and restore procedures. Credentials would remain outside the repository.

## Initial plan

1. Confirm workflows, role permissions, stock units, and acceptance criteria.
2. Design the relational schema and category hierarchy.
3. Implement authentication and server-side access control.
4. Build product, category, and warehouse management.
5. Implement stock receipt, issue, and transactional warehouse transfers.
6. Add movement history, combined filters, dashboard statistics, and alerts.
7. Generate PDF inventory lists from the selected inventory view.
8. Test business rules, database integrity, concurrency, and permissions.
9. Prepare and verify installation in a representative server environment.
10. Document the architecture, results, limitations, and possible extensions.

## Additional information

The initial scope would cover the workflows specified in the brief and prioritise data correctness and a usable interface.

Supplier purchasing, delivery-route optimisation, barcode hardware integration, and external enterprise-system integration would be possible later extensions rather than initial commitments.

My main learning objective is to understand how database constraints, application business rules, transactions, and tests combine to maintain trustworthy inventory information.

Project repository: https://github.com/lehansu755-a11y/Design-and-implementation-of-an-inventory-tracking-and-logistics-management-platform
