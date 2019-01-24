# Re-import APIKit

When changes have been made to a RAML specification in Design Center, the MuleSoft project will need to be updated.

While it may be tempting to manually update the `src/main/resources/` folder manually, it is highly unrecommended to do so.

## Steps

The following steps will assume a project named `exp-business` that uses a domain project.

### Update main flow with new endpoints

1. Copy the configuration XML of `src/main/mule/exp-business.xml` file
1. Delete `exp-business.xml`
1. Re-import RAML from Design Center
1. Open the newly created `exp-business.xml` file
1. Delete the default Transform Message flows in all the endpoints
1. Return to the configuration XML copied in step 1
1. Copy and paste all the endpoint `<flow>` items from the old configuration XML into the new configuration XML
    1. Be sure to only copy over existing endpoints; if new endpoints were added, do not overwrite those
    1. If prompted to generate new doc ids, select _no_

### Update configurations

1. Delete the `exp-business-console` flow
1. If the HTTP Listener configuration is in the domain project, update the Listener in `exp-business-main` flow
    1. Delete the auto generated HTTP Listener Configuration created in `exp-business.xml`
1. Update the _Path_ variable in the Listener in the `exp-business-main` flow