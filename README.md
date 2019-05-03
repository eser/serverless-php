# [serverless-php](https://github.com/eserozvataf/serverless-php)
[![serverless][badge-serverless]](http://www.serverless.com)
[![language][badge-language]](http://php.net)
[![license][badge-license]](LICENSE)

[PHPKonf 2019](http://phpkonf.org) Konferansında sunacak olduğum "Serverless PHP" konuşmasının demo sunumudur.

## Çalıştırmak için adımlar:

- Öncelikle sisteminizde node.js'in ve git komut satırı araçlarının kurulu olduğundan emin olun,

```sh
$ npm install serverless -g
```

- Amazon Web Services'dan Access Keylerinizi temin edin,

```sh
$ serverless config credentials --provider aws --key KEY --secret SECRET
```

veya halihazırda `aws-cli` kullanıcısıysanız

```sh
$ aws configure
AWS Access Key ID [None]: KEY
AWS Secret Access Key [None]: SECRET
Default region name [None]: eu-west-1
Default output format [None]: 
```

komutları ile AWS hesabınızı serverless.js'e tanıtın.

- Bu demoyu git aracılığı ile klonlayın.

```sh
$ git clone https://github.com/eserozvataf/serverless-php
$ cd serverless-php
```

- Demo klasörüne composer bağımlılıklarını indirin.

```sh
$ composer install -o --no-dev
```

- `serverless.yml` dosyası içerisine bir göz gezdirin.

- Serverless.js aracılığı ile deployment'i başlatın.

```sh
$ sls deploy
```

## İhtiyaç halinde PHP'i tekrar derlemek

Bazı durumlarda PHP'i tekrar compile etmeniz/derlemeniz gerekebilir, bunun için mutlaka
[Docker](https://docker.com) kurulu bir cihaz üzerinde işlem yapmanız gerekecektir. Bu
işlemden önce kod tabanında bulunan `buildphp.sh` ve `dockerfile.buildphp` dosyalarını
da incelemeniz gerekebilir.

```sh
$ sh buildphp.sh
```

## Loglara erişmek:

Bir kere deploy işlemi yaptıktan sonra ilgili fonksiyona gelecek requestleri aşağıdaki komut ile izleyebilirsiniz.

```sh
$ sls logs -f hello -t
```

hello burada izleyeceğimiz fonksiyonun ismi.

## Bir işlevi lokal olarak çalıştırmak:

```sh
$ sls invoke local -f hello
```

## Bir işlevi AWS üzerinde çalıştırmak:

```sh
$ sls invoke -f hello
```

## İptal etmek:

Deploy ettiğiniz bir projeyi komple geri çekmek için aşağıdaki komutu kullanabilirsiniz:

```sh
$ sls remove
```

# Teşekkür
[Robert Anderson](https://github.com/ZeroSharp/serverless-php) ve [Andy Raines](https://github.com/araines/serverless-php)'e
bu referans aldığım projeleri için teşekkürlerimi iletiyorum.


[badge-serverless]:   http://public.serverless.com/badges/v3.svg
[badge-language]:     https://img.shields.io/badge/language-php-blue.svg
[badge-license]:      https://img.shields.io/badge/license-MIT-orange.svg
[badge-support-full]: https://img.shields.io/badge/support-full-green.svg
[badge-support-part]: https://img.shields.io/badge/support-partial-yellow.svg
[badge-support-none]: https://img.shields.io/badge/support-none-red.svg
