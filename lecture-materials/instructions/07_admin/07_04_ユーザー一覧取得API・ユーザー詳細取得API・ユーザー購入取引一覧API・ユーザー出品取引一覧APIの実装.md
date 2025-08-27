# 各APIのテストコードのファイルの実装
cp -a larashop-server-completed/tests/Feature/Controllers/Admin/API/UserController/ larashop-server/tests/Feature/Controllers/Admin/API/UserController/

dockerコンテナ内で
php artisan test

# 各APIのルーティング実装。UserControllerの4アクション分
larashop-server/routes/admin_api.php の
 - 30行目の /users のコメントアウトを解除
 - 31行目の /users/{user} のコメントアウトを解除
 - 32行目の /users/{user}/purchased_deals のコメントアウトを解除
 - 33行目の /users/{user}/listed_deals のコメントアウトを解除

# 管理画面側のUserControllerの実装
cp larashop-server-completed/app/Http/Controllers/Admin/API/UserController.php larashop-server/app/Http/Controllers/Admin/API/UserController.php

# 管理画面側のUserServiceInterfaceの宣言とUserServiceの実装
cp -a larashop-server-completed/app/Services/Admin/UserService/ larashop-server/app/Services/Admin/UserService/

# ServiceクラスのDIの設定
larashop-server/app/Providers/ServiceAdminServiceProvider.php の、
 - 24~27行目のUserServiceInterfaceの設定部分のコメントアウト解除

# テストグリーンの確認
dockerコンテナ内で
php artisan test
して、グリーンになったことを確認する