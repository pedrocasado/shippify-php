This library allows you to quickly use Shippify API with PHP

# Install

    composer require pedrocasado/shippify-php

# Usage
    
## Create Shippify object

    $shippify = new \Shippify("api_key", "api_secret");

## List warehouses

    $response = $shippify->get("/warehouse/list");
    var_dump($response);

## Create new Task

    $args['task']['products'] = array(
        [
            'id' => '11',
            'name' => 'Product Name',
            'qty' => 1,
            'size' => 3, // 1 - Bicycle, 2 - Motorcycle, 3 - Car, 4 - SUV, 5 - Truck.. (int) (shippify-package-size)
        ]);

    $args['task']['sender']['email'] = 'we@company.com';

    $args['task']['recipient']['name'] = 'Customer Name';
    $args['task']['recipient']['email'] = 'customer@gmail.com';
    $args['task']['recipient']['phone'] = '22222222';

    $args['task']['pickup']['warehouse'] = 721;
    // $args['task']['pickup']['lat'] = -22.907922;
    // $args['task']['pickup']['lng'] = -43.110450;
    // $args['task']['pickup']['address'] = 'Rua Coronel Moreira Cesar, 250';

    $args['task']['pickup_date'] = strtotime('+1 day');
    $args['task']['deliver']['lat'] = -22.966658;
    $args['task']['deliver']['lng'] = -43.180721;
    $args['task']['deliver']['address'] = 'Rua Curitiba 1957, Lourdes';

    $args['task']['delivery_date'] = strtotime('+2 day');
    $args['task']['payment_type'] = 1;
    $args['task']['payment_status'] = 1;
    $args['task']['ref_id'] = 222323;
    
    $response = $shippify->post("/task/new", $args);
    var_dump($response);

Api documentation: [https://docs.logistics.shippify.co](https://docs.logistics.shippify.co)