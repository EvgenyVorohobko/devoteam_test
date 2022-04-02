# devoteam_test

Steps to work with package.
  1. Download package and deploy it to the own org.
  2. Create custom tab to custom object: Custom Object A (Setup -> Tab -> Create new Custom Object Tab)
  3. Add customRelatedListCmp to the Custom Object A Page.
  4. Use code below to create records:
```
        Custom_Object_A__c customObjA = new Custom_Object_A__c(
            Name = 'Lorem Ipsum A'
        );
        insert customObjA;

        List<Custom_Object_B__c> customObjBs = new List<Custom_Object_B__c>();
        for (Integer i = 1; i < 5000; i++) {
            customObjBs.add(new Custom_Object_B__c(
                Name = 'Lorem Ipsum B ' + i
            ));
        }
        insert customObjBs;

        List<Custom_Object_C__c> customObjCs = new List<Custom_Object_C__c>();
        for (Custom_Object_B__c objB : customObjBs) {
            customObjCs.add(new Custom_Object_C__c(
                Name = 'Lorem Ipsum B ' + objB.Name
            ));
        }
        insert customObjCs;
```
