<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

<b>Requirement/Persyaratan</b>
---
> #### Php versi 8
>> - Cara menginstal php dalam bahasa indonesia : <a href="https://youtu.be/Uw3ZGIMvIdA?si=mBVZ-lBnoCilASzo">install php
>> - Cara menginstal php dalam bahasa inggris : <a href="https://youtu.be/MPRLUd8Pmyo?si=FqN54nVr4duH4Keg"> install php
-----
> #### Laravel versi 10.2.5
>> - cara menginstal laravel yang versi yang sama : 
>>   ```
>>   composer create-project laravel/laravel=v10.2.5 belajar-laravel-eloquent
>>   ```
---
<b>Materi/Bahan</b>
---
> #### Eloquent api resource
> - Eloquent API Resource adalah alat dalam Laravel untuk mengatur dan menampilkan data dari model dalam format yang sesuai untuk respons API. Ini memungkinkan Anda mengontrol dengan tepat bagaimana data disajikan dalam respons API, termasuk properti yang disertakan, disembunyikan, dan format data yang diinginkan.
---
> #### Model
> - model dalam Laravel adalah representasi kelas dari entitas basis data, sedangkan Eloquent API Resource adalah alat untuk mengatur dan menampilkan data dari model dalam format yang sesuai untuk respons API.
---
> #### Resource
> - Resource dalam Laravel adalah kelas yang mengelola dan memformat data untuk respons API. Mereka memungkinkan Anda menyesuaikan bagaimana data disajikan, mengubah format, dan melakukan transformasi sebelum dikirimkan ke klien. Ini membantu menjaga kode Anda terorganisir dan memberikan kontrol atas representasi data dalam API Anda.
---
> #### Resource Collection
> - Resource collection dalam Laravel adalah kelas yang membantu Anda mengelola kumpulan data yang akan dikirim sebagai respons API. Mereka memungkinkan penyesuaian format dan transformasi data sebelum dikirimkan ke klien, menjaga kode Anda tetap terstruktur dan bersih.
---
> #### Nested Resource
> - Nested Resource dalam Laravel adalah cara untuk mengelola hubungan bersarang (nested) antara model dalam respons API. Ini terutama berguna ketika Anda memiliki hubungan one-to-many atau many-to-many antara model, di mana satu model terkait dengan satu atau lebih instance dari model lainnya.
> - Dengan Nested Resource, Anda dapat menyusun respons API sedemikian rupa sehingga model bersarang disertakan dalam respons saat meminta model utama. Ini memungkinkan Anda untuk menggabungkan data yang terkait dan memudahkan klien dalam mengakses informasi yang terkait secara terstruktur.
> - Secara praktis, Nested Resource memungkinkan Anda untuk mengatur respons API dalam struktur yang lebih terorganisir dan bermakna, membantu klien dalam bekerja dengan data yang terhubung.
---
> #### Data Wrap
> - Data wrapping adalah proses menyertakan data tambahan di dalam respons API. Ini dapat berguna untuk menyediakan informasi tambahan kepada pengguna, seperti metadata, pesan status, atau data lain yang relevan dengan respons yang dikirimkan.
> - Dalam konteks Laravel, Anda bisa menggunakan konsep data wrapping dengan resource. Misalnya, Anda bisa membuat wrapper untuk respons API Anda dengan menambahkan data tambahan di samping data utama yang dikirimkan.
> - Berikut adalah contoh sederhana menggunakan data wrapping dalam respons API dengan Laravel:
>  ```
>  use App\Http\Resources\PostResource;
>
>public function show($id)
>{
>    $post = Post::find($id);
>    
>    // Data wrapping dengan resource
>    return response()->json([
>        'data' => new PostResource($post),
>        'status' => 'success',
>        'message' => 'Data post berhasil diambil.'
>    ]);
>}
>```
> - Dalam contoh di atas, selain menyertakan data post yang diambil dari database dengan bantuan resource `PostResource`, kami juga menambahkan informasi status dan pesan ke dalam respons. Ini membuat respons API lebih informatif dan mudah dipahami oleh klien yang menerima respons tersebut.
> - Data wrapping membantu Anda memberikan konteks tambahan kepada pengguna API Anda, membuat pengalaman pengguna lebih baik dan memfasilitasi debugging dan penggunaan API yang lebih baik.
---
> #### Data Wrap Collection
> - Data wrap collection adalah proses menyertakan data tambahan di dalam koleksi data yang dikirim sebagai respons API. Ini berguna untuk memberikan informasi tambahan kepada pengguna, seperti metadata, pesan
status, atau data lain yang relevan dengan koleksi yang dikirimkan.
> - Dalam konteks Laravel, Anda dapat menggunakan konsep data wrap collection dengan menggunakan resource collection. Resource collection memungkinkan Anda untuk menyesuaikan format respons untuk koleksi data.
> - Berikut adalah contoh sederhana menggunakan data wrap collection dalam respons API dengan Laravel:
> ```
> use App\Http\Resources\PostResource;
>
>public function index()
>{
>    $posts = Post::all();
>    
>    // Data wrap collection dengan resource collection
>    return response()->json([
>        'data' => PostResource::collection($posts),
>        'status' => 'success',
>        'message' => 'Data posts berhasil diambil.'
>    ]);
>}
>```
> - Dalam contoh di atas, kami menggunakan resource collection `PostResource::collection($posts)` untuk membungkus data post yang diambil dari database. Selain itu, kami juga menyertakan informasi status dan pesan ke dalam respons.
> - Dengan menggunakan data wrap collection, Anda dapat memberikan informasi tambahan kepada pengguna API Anda, membuat respons API lebih informatif dan mudah dipahami.
---
> #### Pagination
> - Pagination adalah proses membagi hasil query menjadi sejumlah halaman yang dapat ditampilkan, sehingga memungkinkan pengguna untuk menavigasi melalui data dengan lebih mudah. Ini sangat penting ketika Anda memiliki kumpulan data yang besar, karena memungkinkan pengguna untuk mengakses data secara bertahap, mengurangi waktu loading dan memperbaiki kinerja aplikasi secara keseluruhan.
> - Dalam Laravel, Anda dapat menggunakan fitur built-in untuk pagination dengan sangat mudah. Berikut adalah contoh sederhana menggunakan pagination dalam respons API dengan Laravel:
> ```
> use App\Models\Post;
>use App\Http\Resources\PostResource;
>
>public function index()
>{
>    $posts = Post::paginate(10); // Menentukan jumlah item per halaman (10)
>
>    return PostResource::collection($posts);
>}
>```
> - Dalam contoh di atas, kita menggunakan metode `paginate(10)` pada model `Post` untuk mengatur pagination dengan 10 item per halaman. Kemudian, kita menggunakan `PostResource::collection($posts)` untuk mengonversi koleksi post menjadi respons API dengan format yang ditentukan oleh resource.
> - Dengan menggunakan pagination, Anda dapat membagi data ke dalam halaman-halaman kecil yang dapat diakses pengguna secara bertahap, sehingga meningkatkan kinerja dan pengalaman pengguna.
---
> #### Conditional Attributes
> - Conditional attributes dalam Laravel Resource adalah cara untuk menyertakan atribut dalam respons API berdasarkan kondisi tertentu. Ini berguna ketika Anda ingin menyertakan atribut hanya jika kondisi tertentu terpenuhi.
> - Berikut adalah contoh sederhana menggunakan conditional attributes dalam Laravel Resource:
> ```
> use Illuminate\Http\Resources\Json\JsonResource;
>
>class PostResource extends JsonResource
>{
>    public function toArray($request)
>    {
>        return [
>            'id' => $this->id,
>            'title' => $this->title,
>            'content' => $this->when($this->is_published, $this->content), // Hanya menyertakan content jika post is_published
>            'created_at' => $this->created_at,
>            'updated_at' => $this->updated_at,
>        ];
>    }
>}
>```
> - Dalam contoh di atas, kami menggunakan metode `when()` untuk mengatur atribut 'content' sehingga hanya disertakan dalam respons jika kondisi `$this->is_published` terpenuhi. Artinya, jika posting tersebut dipublikasikan (`$this->is_published` bernilai `true`), atribut 'content' akan disertakan dalam respons; jika tidak, atribut tersebut akan diabaikan.
> - Dengan menggunakan conditional attributes, Anda dapat menyediakan fleksibilitas dalam menyusun respons API sesuai dengan kondisi tertentu, menjaga respons Anda tetap bersih dan relevan.
---
> #### Resource Response
> - Resource response dalam konteks Laravel adalah respons yang dihasilkan oleh menggunakan resource untuk memformat data sebelum dikirimkan sebagai respons dari endpoint API. Resource digunakan untuk mengubah representasi model menjadi format yang diinginkan sebelum dikirimkan ke klien.
> - Berikut adalah contoh sederhana penggunaan resource response dalam controller Laravel:
> ```
> use App\Http\Resources\PostResource;
>use App\Models\Post;
>
>public function show($id)
>{
>    $post = Post::findOrFail($id);
>
>    return new PostResource($post);
>}
>```
> - Dalam contoh ini, `PostResource` digunakan untuk memformat data dari model `Post` sebelum dikirimkan sebagai respons API. Resource ini akan mengatur struktur dan format data yang akan dikirimkan ke klien sesuai dengan kebutuhan yang ditentukan di dalam kelas `PostResource`. Dengan menggunakan resource response, Anda memiliki kontrol penuh atas bagaimana data disajikan dalam respons API Anda, memudahkan klien untuk menggunakan data tersebut.
---
<b>Terima Kasih</b>
---
