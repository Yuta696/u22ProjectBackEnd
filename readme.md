# U22 AR図鑑ーLaravelーバックエンド

## 概要

開発環境

[https://arpic-web-api.herokuapp.com/](https://arpic-web-api.herokuapp.com/) 


### 使用技術

バックエンド

* laravel

フロントエンド

* Vue-js

開発環境

* Heroku

### 開発手順

#### DB作成

DBとModelを作成

```
   php artisan make:Model Models/[Model名] -m
```

DBのデータを書き込む
(DBを再構築するもこのコマンドを使います)

```
   php artisan migrate:fresh --seed
```

migrateファイルのサンプル

```
    //ここはDB構築する時、実行するメゾット
    public function up()
       {
           Schema::create('users', function (Blueprint $table) {
               $table->increments('id');
               $table->string('name');
               $table->string('email')->unique();
               $table->timestamp('email_verified_at')->nullable();
               $table->string('password');
               $table->rememberToken();
               $table->timestamps();
           });
       }
       
    
        /**
            * Reverse the migrations.
            *
            * @return void
            */
            
           public function down()
           {
               Schema::dropIfExists('users');
           }
       
```

Modelの作る手順

ユーザーモデルのサンプル

```
   /**
       * The attributes that are mass assignable.
       *
       * @var array
       */
      protected $fillable = [
          'name', 'email', 'password',
      ];
  
      /**
       * The attributes that should be hidden for arrays.
       *
       * @var array
       */
      protected $hidden = [
          'password', 'remember_token',
      ];
```

Modelに連結したいDBを指定（基本上のコマンド使えば、ここは要らない）

```
  protected $table = 'users';
```

DBに更新したい項目を指定


```
  protected $fillable = [
          'name', 'email', 'password',
      ];
```

セキュリティのため、データを隠したい項目

```
  protected $hidden = [
          'password', 'remember_token',
      ];
```



