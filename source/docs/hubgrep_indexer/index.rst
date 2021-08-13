HubGrep Indexer
===============

The indexer is the backend for the various repository crawlers.

It distributes the ids of the repositories that we need to fetch to the crawlers, and collects the results.
Everytime a hoster is finished, it generates an export of the data, so that HubGrep Search can fetch this as an update for its search index.

Deployment
----------

.. toctree::
   deployment/deployment
   :maxdepth: 5

Development
-----------

.. toctree::
    development/API
    :maxdepth: 2


