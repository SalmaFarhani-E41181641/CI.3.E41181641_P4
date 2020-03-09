# CI.3.E41181641_P4
 
# CodeIgniter RestServer

# Yang perlu dipersiapkan dalam penggunaan codeigniter restserver
1.	Web server yakni xampp, wampp ver 7.1 atau keatas, dll
2.	Codeigniter ver. 3.1.11
3.	Visual studio code
4.	Postman 
5.	Library restserver dapat diunduh melalui https://github.com/chriskacerguis/codeigniter-restserver atau https://github.com/ardisaurus/ci-restserver.

# Cara instalasi:
1. Download library restserver
2. Extract codeigniter dan library restserver dan pindahkan ke dalam localhost komputer
3. Tambahkan code berikut ke dalam controller
```use Restserver\Libraries\REST_Controller;```
4. Extend kelas  controller seperti berikut
```class Kontak extends REST_Controller```

# Contoh penggunaan GET dalam rest api:
1.	Buat controller dengan code seperti berikut:
```<?php

defined('BASEPATH') OR exit('No direct script access allowed');

require APPPATH . '/libraries/REST_Controller.php';
use Restserver\Libraries\REST_Controller;

class Kontak extends REST_Controller {

    function __construct($config = 'rest') {
        parent::__construct($config);
        // memanggil atau load database
        $this->load->database();
    }

    //Menampilkan data kontak dengan menggunakan function gets
    function index_get() {
        $id = $this->get('id');
        if ($id == '') {
            $kontak = $this->db->get('telepon')->result();
        } else {
            $this->db->where('id', $id);
            $kontak = $this->db->get('telepon')->result();
        }
        $this->response($kontak, 200);
    }```

2.	Cek penggunaan get dengan postman dengan cara:
![Capture1](https://user-images.githubusercontent.com/55653499/76197497-d62c7480-621e-11ea-9680-5ea32d0ce62c.PNG)
cek function get dengan memanggil id:

![Capture](https://user-images.githubusercontent.com/55653499/76197532-e6dcea80-621e-11ea-8ddd-99033e5e913b.PNG)


  
