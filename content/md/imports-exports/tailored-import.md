---
id: tailored-import
themes: import-export-data
title: Tailored import - **import any file structure** to Akeneo PIM
popular: false
ee: true
ge: true
related: imports, monitor-jobs, access-rights-on-imports-exports
---

# Overview

Tailored Imports is a new import profile that is available to all SaaS users (Enterprise and Growth Edition).
It helps you to import your product information in XLSX <!--or CSV -->files, with different structures to what the PIM usually accepts.  
For instance, let's assume your supplier or brand sends you their product information in different XLSX files; each with different structures:  
* Supplier A sends a file with columns named: "Product ID", "Model Name", "Online description", and "Color".
* Brand B sends a file with columns named: "Gencod", "Web title", "Long label", "Web description", "Supplied accessories".  

**Without** Tailored Import and using a regular import profile, you have to manually modify everything. Transforming your spreadsheet in order to transform your attributes from label to code. Transforming labels, converting measurements, along with many more manual operations.

Thanks to Tailored Import, you can configure all your needs (mapping, operations) via an import and use it as often as necessary. **You no longer need to manually edit your XLSX <!-- or CSV files -->when you need to import product information.**

:::tips
To learn more about Tailored Import and how to use this feature, please watch our training video [Tailored Imports](https://akademy.akeneo.com/tailored-imports).
:::

:::info
Tailored Import is a feature which will be updated all along the year.
So far, the following attribute types aren't available to be mapped: `Price`, `Reference entity multi-select`, `Reference entity single-select`, `Asset collection`, `Table`, `File` & `Image`.
So far, the following system properties aren't available to be mapped: `Parent`, `Family variant`, `Groups` & `Associations`.
Finally, please note we don't support media files import for now.
:::

# Create a Tailored Import profile

To create a new import profile:
1. Go to `Imports`
1. Click on `Create import profile`
1. Type a unique import code and a label, then select the job `Tailored product import`<!-- or `Tailored product model import`-->. <!--You can select either CSV or XLSX for each job.-->
![Create a new product import profile](../img/Tailored-Import_Create-import-profile.png)
1. Save your new import profile

# Edit a Tailored Import profile

Once you've created your Tailored Import profile, or if you want to edit an existing one:
1. Go to `Imports`
1. Click on the Tailored Import profile that you want to edit
1. Click on `Edit` located in the top right corner of the screen  

# Discover the different tabs of this profile

A Tailored Import profile displays the following tabs:
* `Properties`: To name your import profile.
* `Permissions`: To set permissions to allow specific user groups to execute or edit your import profile (Enterprise Edition only).
* `Global settings`: To define the behavior in case an error occurred: you can either skip the products (the rows won't be imported), or skip the values only (the faulty cells won't be imported). Please note in some cases, depending on the error, whole rows could be skipped even though "Skip values" is selected.
* `Import structure`: To create your import structure (read how to [define your import structure](tailored-import.html#define-your-import-structure)).
* `History`: To display the modifications made by any user on your export profile.


# Define your import structure

In the `Import structure` tab, you can define the structure of your file so that it matches all the future files that you will import.
To do that, on one hand you will need to import a file to define the structure and then create your mappings and operations, by adding PIM attributes and linking them to your file columns. On the other hand, after this initial configuration has been done, you will be able to directly import all the product files that share the same structure.

:::warning
Please note that once you define and confirm the structure of your import profile, you won't be able to change it. For instance, if the next file you want to import has a different column order or an extra column, you won't be able to use this import profile and you will have to create another one.
:::

To do this, please follow the steps below:
1.  Under `Import structure` tab, click on `Initialize import structure`
![Initialize import structure](../img/Tailored-Import_Initialize-import-structure.png)
1.  Now, upload the file you need to import. This step will help the PIM to assess the structure of your file. Note that the products in the uploaded file won't be imported at this step.
    ::: info
    Limitations have been set for each uploaded file:
    * Maximum of 500 columns.
    * Maximum 10 MB file size for the structure initialization.
    * Maximum 50 MB file size for product import.
    :::
1.  Once uploaded, you'll have to set different fields:
    * The appropriate sheet in your spreadsheet.
    * The row where the header is located.
    * The row where the first product is displayed.
    * The column where the first product information is displayed.
    * The unique identifier column (this column will be automatically mapped to the "SKU" attribute in the PIM).
    ::: warning
    Before you click on `Confirm`, please verify your configuration. Once this step has been confirmed, you won't be able to change it and you would have to create another import profile if you want to set it differently.
    :::
1. Click on `Confirm` and you'll notice the mapping structure already has an attribute mapped. This attribute is the SKU which was selected in the step 3 above.

::: info
Limitations have been set for each Tailored Import profile:
* Maximum 500 columns.
* You can add up to 4 sources in a single column.
* Text fields are limited to 255 characters.
:::

# Start mapping your columns to your attributes

1. Now it's time to map all the relevant information from your file to the PIM. To do that, click on `Add attribute` and select an attribute from the PIM that you would like to use, for instance the "Name" attribute.
1. Then, you'll see the right panel of this attribute displays three different sections: `Target`, `Source(s)` and `Operation(s)`.
    * The target section will display different settings depending on the attribute you selected in the step above. Read more about ([conditional settings](tailored-import.html#conditional-settings)).
    * The Source(s) section displays all the columns that were found in your uploaded spreadsheet.
    * The Operation(s) section will display one or more operation(s) to transform your data, depending on the target you selected.
1. Click on `Add a source` and select a source listed from your file. The letter between brackets indicates the column where this source is located in your spreadsheet. For instance, select the one that matches the name of your product, e.g. "Web title".
1. Now look at the "Operation(s)" section where the first data samples are displayed as a preview. This preview will display random data samples from the uploaded file enabling you to ensure confirmation of  the sources that you've added to this target.
![Input data sample preview](../img/Tailored-Import_Imput-data-sample-preview.png)
    ::: info
    Data samples are unique values selected randomly from the first 1,000 rows found in the file uploaded for the configuration.
    :::
1. If required, you can add operations under the data samples. Click on `Add operation` and select the one you'd like. Please note that the operations are available depending on the attribute selected as a target, but also depending on previously added operations.
1. At the end of the operations, an output preview of the sample data will be shown, with changes according to the operations that you've added.
![Output data sample preview](../img/Tailored-Import_Output-data-sample-preview.png)
1. Once you're done, click on `Save` in the top right corner. You're now ready to import your products.

### Conditional settings

Depending on the target you selected, some other parameters can be displayed:
* For scopable and/or localizable attributes, you will need to select to which channel and/or locale you want to import your data. ![Target settings - scopable/localizable](../img/Tailored-Import_settings-scopable-localizable.png)
* For collection attributes (multi-select, categories), in case the products in your PIM already exists with a few values, you have the possibility to choose if you want to add the data from your file to the existing data, or if you want to replace the data in the PIM by the one from the file. ![Add or replace exiting data](../img/Tailored-Import_Add-Replace-existing-data.png)
* For each target, the checkbox "Clear if empty in file" helps you decide if you want to clear the product value in your PIM when the cell in your file to import is empty. ![Target settings - clear value if empry](../img/Tailored-Import_settings-clear-if-empty.png)


# Import your products

To launch your import profile, in the breadcrumb, click on the name of your import profile, drag & drop your file and click on `Upload & import now`.
![Upload & import](../img/Tailored-Import_Upload&Import.png)

::: info
Limitations have been set for each uploaded file:
* Maximum of 500 columns.
* Maximum 50 MB file size.
:::

# Discover operations

You can use operations to transform the data in order to make the import process easier.

:::info
New operations will come along the year to help you save time importing your product information. Do not hesitate to contact your Customer Success Manager if you want to help us by communicating your use case & needs.
:::

Depending on the targets that you define, here are the different types of operations that you can add:

## Yes/No replacement

Replace the default values with your own value (only available for the "Yes/No" attribute or the "Enabled" system property).
![Yes/No replacement operation](../img/Tailored-Import_Yes-No_Replacement.png)

## Replacement

Replace the values by your own (only available for simple select, multi select<!--, reference entities single link or multiple link--> attributes).
![Replacement operation](../img/Tailored-Import_Replacement.png)

## Split

If you want to import different values that are located into the same cell of your spreadsheet, you can use this operation to split the values thanks to a separator: comma (,), semicolon (; ), pipe (|).
![Split operation](../img/Tailored-Import_Split.png)
![Split operation demo](../img/Tailored-Import_Split-demo.gif)

<!--## Use default value when empty

Define a default value when the source value is empty.
![Use default value when empty](../img/TailoredExport_Operation_UseDefaultValueWhenEmpty.png)-->

<!--## Conversion

Convert measurement units within the same measurement family (only available for measurement attributes used as a source).
![Conversion](../img/TailoredExport_Operation_Conversion.png)-->

<!--## Rounding

Round measurements values, choosing from `Round`, `Round up` & `Round down` and define the number of digits - up to 12 - after the decimal separator (only available for measurement attributes used as a source).
![Rounding](../img/TailoredExport_Operation_Rounding.png)-->

<!--## Concatenation

Concatenate different sources by displaying up to 4 per column. Click on `Add text` to add more details and create a separation between sources.
![Concatenate](../img/TailoredExport_Operation_Concatenate.gif)-->

## Clean HTML tags

Clean automatically all the HTML tags in your text values.
![Clean HTML tags operation](../img/Tailored-Import_Clean-HTML-tags.png)

<!--:::warning
If you added a default value with HTML tags thanks to the `Use default value when empty operation`, and if you checked `Clean HTML tags` for the same source, this operation won't clean the HTML tags for the default value.
:::-->

# Duplicate a Tailored Import profile

If you want to create another import profile based on an existing one, you can duplicate it.
Please note that the structure of this import profile will remain unmodifiable. You will only be able to add or remove operations, targets and sources.

To do this, please follow the steps below:
1. Select the import profile you would like to duplicate
1. Click on `Edit`
1. In the top right corner, click on the three dots "..." and select `Duplicate`
1. Write a label and a code then click on `Save`
