# 各APIのテストコードのファイルの実装
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/MeController/GetPurchasedProductsTest.php larashop-server/tests/Feature/Controllers/Larashop/API/MeController/GetPurchasedProductsTest.php
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/MeController/GetPurchasedProductDealTest.php larashop-server/tests/Feature/Controllers/Larashop/API/MeController/GetPurchasedProductDealTest.php
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/MeController/GetListedProductsTest.php larashop-server/tests/Feature/Controllers/Larashop/API/MeController/GetListedProductsTest.php
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/MeController/GetListedProductDealTest.php larashop-server/tests/Feature/Controllers/Larashop/API/MeController/GetListedProductDealTest.php

dockerコンテナ内で
php artisan test

# 各APIのルーティング実装
larashop-server/routes/larashop_api.php の
 - 33行目の /me/purchased_products のコメントアウト解除
 - 34行目の /me/purchased_products/{product}/deal のコメントアウト解除
 - 35行目の /me/listed_products のコメントアウト解除
 - 36行目の /me/listed_products/{product}/deal のコメントアウト解除

# MeControllerに各アクションの実装
larashop-server/app/Http/Controllers/Larashop/API/MeController.php の、
 - 84~91行目の getPurchasedProducts() アクションのコメントアウト解除
 - 99~103行目の getPurchasedProductDeal() アクションのコメントアウト解除
 - 111~118行目の getListedProducts() アクションのコメントアウト解除
 - 126~130行目の getListedProductDeal() アクションのコメントアウト解除
 - 41行目のDIしようとしてる行のコメントアウト解除
 - 45行目のServiceクラスのインスタンスを代入しようとしてる行のコメントアウト解除

# ProductServiceInterfaceに getPurchasedProductsByUser() getListedProductsByUser() メソッドを宣言
larashop-server/app/Services/ProductServiceInterface.php の、
 - 20行目の getPurchasedProductsByUser() メソッドのコメントアウト解除
 - 24行目の getListedProductsByUser() メソッドのコメントアウト解除

# ProductServiceに getPurchasedProductsByUser() getListedProductsByUser() メソッドを実装
larashop-server/app/Services/ProductServiceInterface.php の、
 - 92~97行目の chasedProductsByUser() メソッドのコメントアウト解除
 - 105~110行目の getListedProductsByUser() メソッドのコメントアウト解除

# テストグリーンの確認
dockerコンテナ内で
php artisan test
して、グリーンになったことを確認する