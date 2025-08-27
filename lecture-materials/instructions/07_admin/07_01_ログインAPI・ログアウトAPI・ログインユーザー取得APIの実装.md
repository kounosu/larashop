# 各APIのテストコードのファイルの実装
mkdir larashop-server/tests/Feature/Controllers/Admin
mkdir larashop-server/tests/Feature/Controllers/Admin/API
mkdir larashop-server/tests/Feature/Controllers/Admin/API/AuthController

cp -a larashop-server-completed/tests/Feature/Controllers/Admin/API/AuthController/ larashop-server/tests/Feature/Controllers/Admin/API/AuthController/

dockerコンテナ内で
php artisan test

# 各APIのルーティング実装。AuthControllerの3アクション分
larashop-server/routes/admin_api.php の
 - 21行目の /auth/signin のコメントアウト解除
 - 23行目と、34行目のコメントアウトを解除
 - 24行目の /auth/signout のコメントアウトを解除
 - 25行目の /auth/me のコメントアウトを解除

# 管理画面側のAuthControllerの実装
mkdir larashop-server/app/Http/Controllers/Admin
mkdir larashop-server/app/Http/Controllers/Admin/API
mkdir larashop-server/app/Http/Controllers/Admin/API/AuthController
cp larashop-server-completed/app/Http/Controllers/Admin/API/AuthController.php larashop-server/app/Http/Controllers/Admin/API/AuthController.php

# 管理画面側のAuthServiceInterfaceの宣言と、AuthServiceの実装
mkdir larashop-server/app/Services/Admin
cp -a larashop-server-completed/app/Services/Admin/AuthService/ larashop-server/app/Services/Admin/AuthService/

# OperationResult DTOクラスの実装
cp -a larashop-server-completed/app/Services/Admin/Dtos/ larashop-server/app/Services/Admin/Dtos/

# ServiceクラスのDIの設定
larashop-server/app/Providers/ServiceAdminServiceProvider.php の、
 - 16~19行目のAuthServiceInterfaceの設定部分のコメントアウト解除

# テストグリーンの確認
dockerコンテナ内で
php artisan test
して、グリーンになったことを確認する

# 管理画面用アカウントを作成するために、seederを使う
cp -a larashop-server-completed/database/seeders/ larashop-server/database/seeders/

dockerコンテナ内で、
php artisan db:seed