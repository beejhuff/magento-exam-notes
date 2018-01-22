# What is the purpose of each of the fields in the core_url_rewrite table?

This is described in detail in the section '3. URL Rewrites -> 2. Describe the URL rewrite process'.

# When does Magento created the rewrite records for categories and products?

This is done inside 'Mage_Catalog_Model_Indexer_Url' in the 'reindexAll()' function.

# How and where does Magento find a matching record for the current request? 

This is described in detail in the section '3. URL Rewrites -> 1. Describe the URL structure/processing in Magento'.