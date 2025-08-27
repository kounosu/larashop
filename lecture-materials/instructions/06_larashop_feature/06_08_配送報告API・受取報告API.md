# 配送報告API・受取報告APIのテストコードのファイルの実装
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/ProductDealController/ReportDeliveryDealTest.php larashop-server/tests/Feature/Controllers/Larashop/API/ProductDealController/ReportDeliveryDealTest.php
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/ProductDealController/ReportReceiptDealTest.php larashop-server/tests/Feature/Controllers/Larashop/API/ProductDealController/ReportReceiptDealTest.php

dockerコンテナ内で
php artisan test

# 配送報告API・受取報告APIのルーティング実装
larashop-server/routes/larashop_api.php の
 - 43行目の /products/{product}/deal/report_delivery のコメントアウト解除
 - 44行目の /products/{product}/deal/report_receipt のコメントアウト解除

# ProductDealControllerに reportDelivery() reportReceipt() アクションの実装
larashop-server/app/Http/Controllers/Larashop/API/ProductDealController.php の、
 - 123~136行目の reportDelivery() アクションのコメントアウトを解除
 - 145~158行目の reportReceipt() アクションのコメントアウトを解除

# DealServiceInterfaceに reportDelivery() reportReceipt() メソッドの宣言
larashop-server/app/Services/DealServiceInterface.php の、
 - 14行目の reportDelivery() メソッドのコメントアウトを解除
 - 15行目の reportReceipt() メソッドのコメントアウトを解除

# DealServiceに reportDelivery() reportReceipt() メソッドの宣言
larashop-server/app/Services/DealService.php の、
 - 131~151行目の reportDelivery() メソッドのコメントアウトを解除
 - 161~181行目の reportReceipt() メソッドのコメントアウトを解除

# テストグリーンの確認
dockerコンテナ内で
php artisan test
して、グリーンになったことを確認する