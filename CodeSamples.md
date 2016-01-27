# Code Samples

## Sample 1 (PHP)

    <?php

    $db = new PDO($dataSource, $dataUsername, $dataPassword, $dataOptions);
    $db->query("select * from articles where id = {$_GET['id']}");

    ?>

## Sample 2 (PHP)

    <?php

    foreach($_REQUEST as $key => $value) {
        include($value);
    }