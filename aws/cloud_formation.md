# CloudFormation
- 概要
  - AWSのリソース管理をコードで行うことができるサービス

- 料金
  - CloudFormationの使用は無料
  - CloudFormationで作成したAWSリソース（EC2、RDSなど）に対して料金がかかる

- メモ
  - Visual Studio Codeで以下のプラグインをインストールすると、スニペットが利用できる
    - CloudFormation
  - 組み込み関数
    - { "Ref": "logicalName" }
      - "logicalName"のパラメーター値を返す
    - { "Fn::Join": [ "delimiter", [ "value1", "value2", "value3" ] }
      - "delimiter"で区切りながら、value1〜valur3を結合する
  - サンプル
    - VPC、subnet*2、EC2*2、立ち上げ
      - 「vpc-subnet-ec2.json」参照
- 参考
  - https://aws.amazon.com/jp/cloudformation/