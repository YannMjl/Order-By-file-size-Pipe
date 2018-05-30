# Order-By-file-size-Pipe

This project contains 2 pipe that help format and display data in Angular.
## Getting Started

These pipes are design for sorting and formating data in Angular projects.

## Usage

### Order By pipe

Create a your_file_name.pipe in you angular project and copy the code need to create the pipe.
Or simply download the file from github and added them to your angular project.

##### In HTML template

```html
{{ collection | orderBy: order : reverse }}
```

### Arguments

| Param | Type | Default Value | Details |
| --- | --- | --- | --- |
| collection | `array` or `object` |  | The collection or object to sort |
| order  | `string` |  | The key or collection of keys to determinate order |
| reverse *(optional)* | `boolean`| false | Reverse sorting order |

Import `OrderModule` to your module

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule  } from '@angular/platform-browser';
import { AppComponent } from './app';

// import pipes
import { OrderByPipe } from './shared/order-by.pipe';
import { FileSizePipe } from './shared/file-size.pipe';


@NgModule({
  imports: [BrowserModule, OrderModule],
  declarations: [
    OrderByPipe,
    FileSizePipe,
    AppComponent
    ],
  bootstrap: [AppComponent]
})
export class AppModule {}

```

In your component

```typescript
// The function setOrder is called in the html page to set to change order

export class AppComponent implements OnInit {
    order: string;
    reverse: boolean;
    array: any[] = [{ name: 'John'} , { name: 'Mary' }, { name: 'Adam' }];
    

    ngOnInit(){
        this.order = 'name';
    }

    setOrder(value: string) {
    if (this.order === value) {
      this.reverse = !this.reverse;
      if (this.reverse === true) {
        value = '-' + value;
      }
    }
    this.order = value;
  }
}
```

## Author

* **[Yann Mulonda](https://github.com/YannMjl)** 

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) © [Yann Mulonda](https://github.com/YannMjl) file for details.
