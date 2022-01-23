# CMS-Pulse-Jilene
https://github.com/seanresolute/CMS-EIT.git

CMS Employee Information Tool (CMS EIT) rebranded to CMS Pulse

How Might We ... alert Center for Medicare & Medicaid Services (CMS) employees of an emergency with web or mobile notifications? 
UX Case Study: https://uxfol.io/p/jilenej/03acb715

# CMS-EIT
This is a Node/EJS/Express project that will play the role as the web application. The current design is MVC.

## Main Artifacts

### /src/views
These are the EJS based views that bind to the route calls. pageTemplate.ejs acts as the master page with the navigation controls. The pages for display are referenced in an "include" reference: <%- include(view) %>. Also references to header and footer ejs.

The page navigation functionality (how to push content to the "include") is referenced below.

All other pages would be housed in here too.

### /src/routes
Contains all of the routing logic for URL requests. There is a general pattern for passing information
```
res.render(
    'pageTemplate',
    {
        view: 'index',
        title: 'EIT Home',
        urgentMsgRS: urgentMsgs.recordset,
        otherMsgRS: otherMsgs.recordset,
        user: req.user
    }
);
```        
We always reference 'PageTemplate' as the primary view.
The JSON message passed to the page will always include attributes:
"view": References the name of the child page.
"user": req.user, which contains session info of the authenticated user.
Anything else needed for referencing data.

### /src/services
Ancillary services, such as authentication logic (auth.js).

## Approach to Developing UI
Application logic, for the most part, will be executed against an API layer leveraging standard REST API calls. I'll update this document with the API signatures - couple of remaining tweaks I need to determine in regards to what the "user" attributes look like. There will be an API key to validate the call.


### Design system
We're using the CMS Design System [design.cms.gov](https://design.cms.gov), with modifications to support a custom theme.
