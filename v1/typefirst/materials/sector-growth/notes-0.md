


* may 24 night 
    * questions
        * do we create orders as draft orders, such that they can be fulfilled by the admin instead of user checkout, or go straight to order?
        * company catalog
            * question: is “catalog” (term doesnt seem to exist) the list of products (what about services)
            * question: products are not associated with companies (only with accounts and with deals as line items)
            * on shopify they have a number of options for catalogs when creating a company. im assuming these mean a set of prices or whatever that this company gets. im guessing we want to get the list of possible catalogs from shopify and sync it into hubspot to use as dropdown options when creating a company, in the same manner as shop. 
        * question: does inventory sync require that we add a custom property to the account products, such that data sync’s “product sync” would be sufficient if it also managed this field? this doesnt currently exist
        * shopify order questions
            * id (account id or something) vs orderid
            * deal record id or something referring to hubspot id? (cant seem to find any such custom property created
            * “names” (D17) and “customer.lastOrderName” are n
            * created an order manually, which they cancelled and then “disabled” my account.. but did go through fulfilment stage
                * what is a “tracking number” (doc)?
                * “shipping carrier” (doc) =?= “shipping line” (shopify)
            * obstacles/blockers:
                * items have prices now
                * we cant seem to create orders as actual users
        * no native variants in hubspot
            * data sync only considers only the primary variant when syncing products
            * how do we do inventory if we dont have variants in hubspot 
            * in order to create an order we have to provide a variant id. this means some solution where we add a custom property to 
    * webhooks setup/test
    * arch 
        * event sourcing services
        * _isologic package like “entities”
        * track api usage
        * actions: webhooks, manuals
        * initialization / terraforming: 
            * do we have all the custom properties created on both sides that we’ll need?
    * UI
        * toggle “future look” disabled features
        * maybe multitenant (whitelabel)
* may 24 plan
    * create base services
            * ledger
                * consumers can reduce entries (with filters: time range, type, limit, etc) 
                * consumers can make entries (which includes their own projections and general state)
            * config (static + dynamic) (reads/writes to ledger)
        * * services create their own projections, using ledger service

plan



* build ui with all the extra  out disabled features you can think of, but have a toggle setting to make them all disappear so you see what it looks like with only enabled features. this should also generally work as a feature-toggling mechanism in the future (keep it simple for now)
* todo
    * * create sectordev acount for firebase project
    * ** WE HAVE 0 AUTH CAUSE FIREBASE CHANGED UP ON US
    * ** BLAST ENGINE SHIT INSTALLED IN PACKAGE MODULES WITHOUT LINK 
    * clarify and document (find docs)
        * what do we want to do (what data sync)
    * hubspot-> get all data consituting our custom entities and store/updatein fb
        * CRUD OPERATIONS strigaht from db or whatever
        * support chat in dashbard, superuser access (see mouse type movememt) (kind of unneccessary here but great for next project.
        * historical reccord inluding accessibke error logs
            * volume incurred, actvity, error frequency
        * scheduled db scans in case we missed something (in batches)
            * in UI dashaord show next upcoming sync and provide controls to change, trigger, and disable
        * webroots
    * login would be by user/passords
    * shopify
    * nice to have: track duplicates
    * * we need typescript
    * make a script to search through recent terminal commands
    * port as phone app

	⁃		⁃	live support (chat, user impersonation, mouse following)



* add utils-node to build and pull-deps 
* there is no config service in client, configs get fed in individually, is this better possibly? more likely worse