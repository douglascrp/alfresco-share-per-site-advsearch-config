# Introduction #

A common requirement when using Alfresco to keep documents from several customers at the same time is to be able to hide customer specific info from another customers.
When you deploy content model, there are sometimes that you have document types specific to one customer, like "Customer A Document" and "Customer B Document".

What this addon is intended to do is to allow you to configure the types list in advanced search form, per site.
In "Customer A Site", you will be able to show only the types you want, like "Customer A Document".


# Details #

After you deploy the addon, you will be able to use something like this:

In share-custom-config.xml

```
<config replace="true" evaluator="string-compare" condition="AdvancedSearch">
        <advanced-search>
                <!-- Forms for the advanced search type list -->
                <forms>
                        <!-- Shows type only on sites "siteA" and "siteB" -->
                        <form label="Type A" description="Search for Type A" sites="siteA,siteB">sam:typeA</form>
                        <!-- Shows type on "ANY" site -->
                        <form label="Documents" description="Search for Documents" sites="ANY">cm:document</form>
                        <!-- Shows type on user dashboard only -->
                        <form label="Folders" description="Search for Folders">cm:folder</form>
                </forms>
        </advanced-search>
</config>
```

In **sites** tag, you have to set the sites' ids