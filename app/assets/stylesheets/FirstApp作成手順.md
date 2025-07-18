1. アプリケーションの新規作成手順
  1.Railsアプリケーションの新規作成
    Railsアプリケーションを作成
      % rails new アプリケーション名
    Railsのバージョンを指定してアプリケーションを作成(7.1.0の場合)
      % rails _7.1.0_ new アプリケーション名
    データベース管理システムにmysqlを指定
      % rails new アプリケーション名 -d mysql

  2.データベースの作成
    データベースを作成する
      % rails db:create

2. 一覧機能（indexアクション）を実装する手順
  1.ルーティングの設定
    config/routes.rb
      Rails.application.routes.draw do
        get 'posts', to: 'posts#index'
      end
  
  2.設定したルーティングの確認
    % rails routes

  3.コントローラの作成
    rails g controller コントローラー名
    # postsコントローラーを作成
      % rails g controller posts

  4.アクションを定義
    app/controllers/posts_controller.rb
      def index 
      end
  
  5.ビューの作成
    1.app/views/postsディレクトリを選択してindex.html.erbを作成


3. 投稿画面（newアクション）を作成する手順
  1.モデルの作成
    % rails g model post

  2.マイグレーションファイルの編集
    db/migrate/20XXXXXXXXXXXX_create_posts.rb
    class CreatePosts < ActiveRecord::Migration[7.1]
      def updef change
      create_table :posts do |t|
        t.text :memo
        t.timestamps
      end
    end
  end

  3.マイグレーションの実行
    rails db:migrate

  4.ルーティングの設定
    config/routes.rb
      get 'posts/new', to: 'posts#new'
    
  5.アクションを定義
    app/controllers/posts_controller.rb
      def new
      end
  
  6.ビューの作成
    1.app/views/postsディレクトリを選択してnew.html.erbを作成


4. 保存機能（createアクション）を実装する手順
  1.ルーティングの設定
    config/routes.rb
      post 'posts', to: 'posts#create'
  
  2.アクションを定義
    app/controllers/posts_controller.rb
      def create
      end
  
  3.ビューの作成
    1.app/views/postsディレクトリを選択してnew.html.erbを作成
    