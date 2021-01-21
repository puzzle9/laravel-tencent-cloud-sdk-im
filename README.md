# 安装

```bash
composer install puzzle9/laravel-tencent-cloud-sdk-im -vvv
```

## laravel

### 推送配置

```bash
php artisan vendor:publish --tag=laravel-tencentsdk-im
```

## lumen

`bootstrap/app.php`
```php
$app->register(Puzzle9\TencentCloudSdkIm\ServiceProvider::class);
```

### 推送配置

```bash
cp  ./vendor/puzzle9/laravel-tencent-cloud-sdk-im/src/config.php ./config/tencentsdkim.php
```

## 更新 `.env`

```dotenv
TENCENT_TIM_APPID=
TENCENT_TIM_SECRET=
TENCENT_TIM_IDENTIFIER=
```

# 使用

```php
use Puzzle9\TencentCloudSdkIm\TencentCloudSdkIm;

// 获取 user sig
TencentCloudSdkIm::GenUserSig('user_id');

// 帐号
$account = TencentCloudSdkIm::Account();
// 查询帐号
$account->check('user_id');

// ...
```

# 其他
## 截至第一版提交 因 `composer.json` `require` 版本问题 在 `laravel` `6.x` 之后可能安装失败

修改 项目 `composer.json` 为

```json
{
    "prefer-stable": false,
    "repositories": [
        {
            "type": "git",
            "url": "https://github.com/puzzle9/qcloud-im-sdk-php",
            "canonical": false
        }
    ]
}
```

删除 `composer.lock` 和 `vendor` 重新安装即可

# todo
- [ ] 优化 `cache` `log` 部分
- [ ] 让其更人性化一点
- [x] 第一个版本

# 感谢
- <https://github.com/chinayin/qcloud-im-sdk-php>