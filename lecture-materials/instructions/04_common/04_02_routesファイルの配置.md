# ルーティング設定ファイルを、サービスサイト側と管理画面側でファイル分割するため
cp larashop-server-completed/routes/admin_api.php larashop-server/routes/admin_api.php
cp larashop-server-completed/routes/larashop_api.php larashop-server/routes/larashop_api.php
rm larashop-server/routes/api.php
cp larashop-server-completed/app/Providers/RouteServiceProvider.php larashop-server/app/Providers/RouteServiceProvider.php

# Route設定を全て未設定にしておき、あとで実装時にコメントアウト解除
larashop-server/routes/admin_api.php の
 - 21~33行目をコメントアウト

# Route設定を全て未設定にしておき、あとで実装時にコメントアウト解除
larashop-server/routes/larashop_api.php の
 - 21~45行目をコメントアウト