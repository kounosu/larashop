# DBマイグレーションファイル全て実装
cp -a larashop-server-completed/database/migrations/. larashop-server/database/migrations

# DBマイグレーションの実行
dockerコンテナ内で、
php artisan migrate

# Model系ファイル全て実装
cp -a larashop-server-completed/app/Models/ larashop-server/app/Models/

# Enum系ファイル全て実装
cp -a larashop-server-completed/app/Enums/ larashop-server/app/Enums/

#  Factoryファイル全て実装
cp -a larashop-server-completed/database/factories/ larashop-server/database/factories/