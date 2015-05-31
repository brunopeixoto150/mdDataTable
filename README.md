# md-data-table
Angular data table implementation of google material design.

# google data table specification
http://www.google.com/design/spec/components/data-tables.html

# Basic idea 
### (not finalized yet, if you have improvement ideas, let me know)

In its simplest form, a data table contains a top row of column names, and rows for data.

### Table attributes

| Params                                         | ChildParams                     | Type          | Details       |
| ---------------------------------------------- | ------------------------------- | ------------- | ------------- |
| selectable-rows                                |                                 | Boolean       | optional, checkboxes accompany each row if need to select or manipulate data |
| sortable-columns                               |                                 | Boolean       | optional, if enabled, sort data and display a sorted state in the column header. If the user clicks on a column that is already sorted, reverse the sort order and rotate the sort icon. Use sortable-rows-default attribute directive on a column which intended to be the default sortable column |
| column-overflow-handler                        |                                 | String        | optional      |
|                                                | _(default)_ truncateColumnNames | String        |               |
|                                                | useHorizontalScrollingOnTable   | String        |               |
| table-card                                     |                                 | Object        | optional      |
|                                                | title                           | String        |               |
|                                                | actionIcons                     | Boolean       |               |
|                                                | displayPagination               | Boolean       |               |
|                                                | displayPaginationLabels         | Boolean       |               |
|                                                |                                 |               |               |
| alternate-headers                              |                                 | String        | optional      |
|                                                | persistentActions               | -             |               |
|                                                | contextual                      | -             |               |
| table-rows-data                                |                                 | Array         | array representations of data |


### Column attributes

| Params                                         | ChildParams        | Type          | Details         |
| ---------------------------------------------- | ------------------ | ------------- | --------------- |
| column-definition                              |                    | String        | if provided, display a tooltip on hover. If sorting is enabled, display a light sort icon upon hover, which indicates that the column is sortable. |
| inline-menu                                    |                    | Array         | if provided, users can select from a predefined list of options. In this scenario, a menu component directly embedded in the table |
| editable-field                                 |                    | String        | if provided, provides basic text editing. Include editable fields within a table and denote them using placeholder text(if empty). You can use a simple edit dialog with just a text field, or display a full dialog component on click. |
|                                                | textInput          | -             | An editable table cell with placeholder text |
|                                                | smallEditDialog    | -             | A simple, one-field edit dialog on click |
|                                                | largeEditDialog    | -             | A complex, flexible edit edit dialog on click |
|                                                | editIcon           | -             | Inline edit icon |
|                                                |                    |               |                  |
| sortable-rows-default                          |                    | -             | When sortable-columns is applied to the table, it marks the column as the default sorting column |


### Example:
    <md-data-table
        selectable-rows="true"
        table-card="{title: Nutrition, actionIcons: true}"
        table-rows-data="[{Frozen yogurt, iceCream, 159, 6.0, 24, 4.0}]">

        <!-- defining column descriptions -->
        <md-data-table-column column-definition="The total amount of food energy in the given serving size.">
            Dessert (100g serving)
        </md-data-table-column>

        <!-- in case of inline menu -->
        <md-data-table-column inline-menu="[ {iceCream: 'Ice Cream', pastry: 'Pastry', other: 'Other'} ]">Type</md-data-table-column>

        <!-- inline text editing -->
        <md-data-table-column editable-field="textInput">
            Calories
        </md-data-table-column>

        <!-- in case of sortable columns, we can set the defaultly sortable column -->
        <md-data-table-column sortable-rows-default>
            Fat (g)
        </md-data-table-column>
        <md-data-table-column>Carbs (g)</md-data-table-column>
        <md-data-table-column>Protein (g)</md-data-table-column>
    </md-data-table>


# Milestones
- Structure
- Interaction
- Tables within cards
