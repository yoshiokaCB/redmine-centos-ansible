# redmine-amazonlinux2-ansible

Amazon Linux 2 にRedmicaを自動インストールするためのAnsibleプレイブックです。

## 概要

Ansibleを使ってRedmicaを自動インストールするためのプレイブックです。

## システム構成

* Redmica 1.3
* Amazon Linux 2
* PostgreSQL
* Apache


## Redmicaのインストール手順

インストール直後の Amazon Linux 2 にSSMでログインし以下の操作を行ってください。

### Ansibleとgitのインストール

```
sudo yum update -y
sudo amazon-linux-extras install -y epel
sudo yum install -y ansible git
```

### playbookのダウンロード

```
git clone -b redmica https://github.com/yoshiokaCB/redmine-centos-ansible.git
```

### PostgreSQLに設定するパスワードの変更

ダウンロードしたプレイブック内のファイル `group_vars/redmine-servers` をエディタで開き、 `db_passwd_redmine` を適当な内容に変更してください。
これはPostgreSQLのRedmine用ユーザー redmica に設定されるパスワードです。

### playbook実行

下記コマンドを実行してください。Redmineの自動インストールが開始されます。

```
cd redmine-centos-ansible
ansible-playbook -i hosts site.yml
```

10〜20分ほどでインストールが完了します。webブラウザで `http://パブリックIPアドレス/redmine` にアクセスしてください。Redmineの画面が表示されるはずです。


## ライセンス

MIT License

