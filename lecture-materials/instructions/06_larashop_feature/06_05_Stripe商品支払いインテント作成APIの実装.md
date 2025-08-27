# 商品支払いインテント作成APIのテストコードのファイルの実装
mkdir larashop-server/tests/Feature/Controllers/Larashop/API/ProductDealController
cp larashop-server-completed/tests/Feature/Controllers/Larashop/API/ProductDealController/CreatePaymentIntentTest.php larashop-server/tests/Feature/Controllers/Larashop/API/ProductDealController/CreatePaymentIntentTest.php

dockerコンテナ内で
php artisan test

# 商品支払いインテント作成APIのルーティング実装
larashop-server/routes/larashop_api.php の
 - 40行目の /products/{product}/deal/payment_intent のコメントアウト解除

# ProductDealControllerに createPaymentIntent() アクションの実装
cp larashop-server-completed/app/Http/Controllers/Larashop/API/ProductDealController.php larashop-server/app/Http/Controllers/Larashop/API/ProductDealController.php

larashop-server/app/Controllers/Larashop/API/ProductDealController.php の、
 - 74~92行目の verifyPaymentIntent() アクションをコメントアウト
 - 101~114行目の cancel() アクションをコメントアウト
 - 123~136行目の reportDelivery() アクションをコメントアウト
 - 145~158行目の reportReceipt() アクションをコメントアウト

# DealServiceInterfaceの作成と、DealServiceの実装
cp -a larashop-server-completed/app/Services/Larashop/DealService/ larashop-server/app/Services/Larashop/DealService/

# DealServiceInterfaceの、まだ不要なメソッド宣言は一旦コメントアウト
larashop-server/app/Services/Larashop/DealServiceInterface.php の、
 - 12行目の verifyPaymentIntent() メソッドをコメントアウト
 - 13行目の cancel() メソッドをコメントアウト
 - 14行目の reportDelivery() メソッドをコメントアウト
 - 15行目の reportReceipt() メソッドをコメントアウト

# DealServiceの、まだ不要なメソッド実装は一旦コメントアウト
larashop-server/app/Services/Larashop/DealService.php の、
 - 67~91行目の verifyPaymentIntent() メソッドをコメントアウト
 - 101~121行目の cancel() メソッドをコメントアウト
 - 131~151行目の reportDelivery() メソッドをコメントアウト
 - 161~181行目の reportReceipt() メソッドをコメントアウト

# StripeServiceInterfaceの作成と、StripeServiceの実装
# テスト環境用のStripeServiceMockがあることに注目
cp -a larashop-server-completed/app/Services/Larashop/StripeService/ larashop-server/app/Services/Larashop/StripeService/

# ServiceクラスのDIの設定
larashop-server/app/Providers/ServiceLarashopServiceProvider.php の、
 - 20~23行目のDealServiceInterfaceの設定部分のコメントアウト解除
 - 38~48行目のStripeServiceInterfaceの設定部分のコメントアウト解除

# 認可（ユーザーは購入フローを進めることが許可されているか判定）のためのPolicy実装
cp -a larashop-server-completed/app/Policies/ larashop-server/app/Policies/
cp larashop-server-completed/app/Providers/AuthServiceProvider.php larashop-server/app/Providers/AuthServiceProvider.php

# テストグリーンの確認
dockerコンテナ内で
php artisan test
して、グリーンになったことを確認する

# （必須ではない）興味ある方は、Stripeでアカウントを新規登録してテスト環境を作成して、
# 公開可能キーとシークレットキーを設定してみてください
.envの、
 - STRIPE_PUBLISHABLE_KEY環境変数にキーを公開可能キーの文字列をセット
 - STRIPE_SECRET_KEY環境変数にキーをシークレットキーの文字列をセット

Next.js側リポジトリの larashop-nextjs/.env.local の、
 - NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY環境変数にキーを公開可能キーの文字列をセット

yarn dev start
して、環境変数を反映してNext.js再起動