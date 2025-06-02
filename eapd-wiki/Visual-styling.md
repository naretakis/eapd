## This project uses the CMS Design System
Initially, the prototype site was built with a custom-styled flavor of the US Web Design System styles. In December 2018, the team learned that CMS has its own Design System. The [CMS Design System](https://design.cms.gov/) is based heavily on the US Web Design System, but has a robust library of React components, a slightly different suite of interaction components, and uses Open Sans universally instead of Source Sans Pro.  Courier was added as a numerical font after customizing and furthering the complexity of this component. 
- 🔐 [Notes](https://docs.google.com/document/d/18s8qUFb0nugJfNN240Gim3NeORoMchPcIyW9YZuF7QA/edit) from conversation with product manager at CMS, and member of contractor team maintaining the system

## Branding

**Logo** 

The logo utilizes MACPro themes and color to unite branding.  Several iterations were made of this and we landed on a clean, modern, and minimal aesthetic to bring forth accessibility and simplicity to the application.  Included below are uses for color, light variant, and dark variant depending on background and surrounding artifacts.  

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/714b889e-745b-4cb6-94ed-efcd80a77e4d)

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/7200baee-a50b-42ce-b8dd-6d86ff148863)

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/99ffcc42-3bc8-492f-9717-bc09ab8d6a7e)

## Typeface

**Title Case Usage**

We have decided to utilize title case for navigation link elements and titles within the application. 

**Open Sans**
![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/2f2c473e-d3ea-452c-9fa3-10aa7265b9b2)


**Courier**

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/05fe65a5-ac76-4a18-ba98-f5fb87cd8204)

In February 2019, the team [began replacing](https://github.com/18F/cms-hitech-apd/issues/1250) the prototype styles with the new CMS Design System styles and components. We did this in an agile way by starting with the CMS grid, and redesigning isolated components, then sections of the app. 

## Visual/UI design research

- [Audit of interface components and styles](https://app.mural.co/t/gsa6/m/gsa6/1541519041265/08088a073981788567ca9b9edb33412f672144a3) present in the prototyping site (pre-2019)
- [GitHub issue](https://github.com/18F/cms-hitech-apd/issues/1082) evaluating the audit and planning improvements for UI consistency

## Visual styling
The eAPD product is in the Medicaid and CHIP Program ([MACPro](https://www.medicaid.gov/state-resource-center/medicaid-and-chip-program-portal/medicaid-and-chip-program-portal.html)) Program, and ultimately should be associated with it in some way. However, MACPro doesn't have a strong, established visual identity which we could use to inform styling decisions.

You can see the visual styling of the MACPro tool in these YouTube training videos: 
- [MACPro Training Pt 2: Creating State Profile](https://www.youtube.com/watch?v=AXkHXOB1TSc&feature=youtu.be) 
- [MACPro Training Pt 3: Creating an Official Simple Submission Package](https://www.youtube.com/watch?v=VaKwtSIXPPs&feature=youtu.be)

These two videos however showcase a different design system **_Appian_**

### Current visual design strategy
Since the MACPro system doesn't use the CMS Design System yet, the eAPD tool will be a few steps ahead, and can demonstrate what a strong use of the default styles can look like. We have an opportunity to show how much you can accomplish using the "vanilla" CMS Design System. If the team feels it's appropriate to add further customization later, it could inform both this app, and the MACPro tool. Successful visual design choices would not add to the already busy environment of CMS sub-brands and interpretations of the Design System.

### What's different (Current Implementation)
So far we've found that there are areas where our app has more complexity than the stock components from the CMS Design System:

- **Navigation:** Navigation currently is defined as a drop down 3 level tiered system.  We've made the decision not to add unnecessary layers to detract from the user experience and confuse the user where to navigate.  

Future styling may consider https://github.com/CMSgov/design-system/issues/742 super nav. but this has not been discussed yet.

- **Tables:** The CMS Design system has [basic tables](https://design.cms.gov/components/table/) built for textual information, formatted with generous white space. The eAPD requires complex, dense tabular data tables, so we've kept our custom styling for now. There's lots of opportunity for optimizing the eAPD table styles, which hasn't been approached yet. 

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/33d60ea2-9b50-41fe-847a-664835964a46)

- **Modals:** The eAPD site provides users with alerts and useful information however any use of modals we've retained our custom styling.

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/e155535b-136f-4095-9df4-dbdee9636d62)

- **Help text blue box design:** The eAPD site differs from the vanilla design system currently.  Instead of a dark blue line on the left hand side of the box per design spec a dark blue triangle is displayed.  This component has been discussed on usage in content reviews, it will be primarily used for examples.

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/56b608f7-cdff-4d68-a968-bf6e209318e3)

- **Removal of iconography from delete hyperlink (variant usage of Delete component):** 

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/515e6027-b837-448f-b6ae-2b0e576bc753)

- **Error Validation Styles:** Incorporation of a different design style to the current CMS Design System with the error text below the form field.  This will contrast to the error text being above the form field.

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/776cb942-e728-49ec-ab93-7034b4b89269)

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/88d6abec-4ea8-40f0-877e-434c0838b087)

### (Future Implementation) Visual Changes

- **Accordion interactions and Table Design Styles:** Consideration will be on a use by use basis for the accordion interaction, USWDS will most likely be the accordion style utilized. 

https://designsystem.digital.gov/components/accordion/

  The table design is being refined and will be rolled out later in the project.

![](https://images.zenhubusercontent.com/5e7151677c78c820a2a11970/f396c7d5-83f4-4ee7-825b-557bea7092c9)



## Design files
The team has built on top of the CMS Design System UI Kit Sketch file, and uses it as a library to power our styled page mockups / before they move to production. The 18F designers will have the latest version of the Sketch file.

(Update) The team has moved to Figma and will be able to supply URL for location of newest design file.  Currently the URL for the Figma file is here.

https://www.figma.com/file/6eVvo7JjvXiovGTR4BoVgK/CMS-eAPD-2020