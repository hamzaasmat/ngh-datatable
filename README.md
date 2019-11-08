# ngh-datatable

Simple lightweight table plugin for angular apps

## Installation

Use the npm to install the plugin.

```bash
npm install ngh-datatable --save
```

## Documentation

### Inputs (Properties)

* `Rows` (`Array<any>`) Only list of rows to be display in table 
* `Column` (`Array<any>`) Array of data for table columns should contains two things 
    * `key:'...'` it will contains the keys from your list of rows
    * `caption:'...'` and the caption which will be used as table heading as `<th></th>`
* `actionArea` (`TemplateRef<any>`) it will specify the action buttons area in `<ng-template>` as `<ng-template #actionArea></ng-template>`
* `tableTitle` (`string`) the title of table
* `showHeader` (`boolean`) to enable the table header `true/false`
* `height` (`number`) height of the table according to the screen - between `1 to 100`
* `loadingIndicator` (`boolean`) a nice loader for table

## Usage

IMPORT NghDatatableModule IN APP MODULE FILE

```python
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { NghDatatableModule } from 'ngh-datatable'

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    NghDatatableModule
  ],

  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }


```
Now in your component where you want to use this plugin will look like this component.html

```python

<ngh-datatable 
    [Rows]="rows" 
    [Column]="column" 
    [title]="Your table tile" 
    [actionArea]="actionArea"
    [loadingIndicator]="loadingIndicator"
    [showHeader]="true">
    <ng-template #actionArea let-item="row">
        //use to add left and right content in table header
        <div headerContentLeft>
            Left content - you can add anything here
        </div>
        <div headerContentRight>
            Right content - you can add anything here
        </div>
        // Your buttons (edit & delete) will go here
        <button type="button" class="table-action-btn" (click)="editEmp(item)">
            Edit
        </button>
        <button type="button" class="table-action-btn" (click)="deleteEmp(item.id)">
            Delete
        </button>
    </ng-template>
</ngh-datatable>

// add below scss code to enable button styling

    .table-action-btn {
        background: white;
        border: none;
        margin: 0 4px;
        display: inline-block;
        box-shadow: 0px 0px 4px rgba(0,0,0,.2);
        cursor: pointer !important;
        outline: none;
        transition: .3s ease-in-out;
        &:hover {
            background: lighten(blue, 30%);
            color: #fff;
        }
    }

```

And in component.ts file 

```python

rows: //some array of data;
column = [
    { key: 'your key from some array of data', caption: 'Display name for column heading' },
    //actionArea column
    { key: 'action', caption: 'Operation' }
]

```

### License

The ISC License