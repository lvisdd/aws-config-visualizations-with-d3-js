## AWS Config について

　AWS公式の[AWS Config](https://aws.amazon.com/jp/config/) のページによると、「AWS Config は完全マネージド型のサービスで、セキュリティとガバナンスのため、AWS リソースインベントリ、設定履歴、および設定変更通知といった機能が用意されています。」とあります。AWSリソースの構成や設定変更の履歴を監査・可視化することが出来ます。

　以下のような構成情報をJSON形式で取得することができます。

```json:aws_config.json
{
    "fileVersion": "1.0",
    "requestId": "asudf8ow-4e34-4f32-afeb-0ace5bf3trye",
    "configurationItems": [
        {
            "configurationItemVersion": "1.0",
                    <中略>
            "accountId": "12345678910",
                    <中略>
            "availibilityZone": "us-west-2b",
            "resourceType": "AWS::EC2::Instance",
                    <中略>
            "configuration": {
                "instanceId": "i-344c463d",
                "imageId": "ami-ccf297fc",
                    <中略>
                "instanceType": "t1.micro",
                    <中略>
                "vpcId": "vpc-41b4cf2a",
                "privateIpAddress": "172.31.21.63",
                "publicIpAddress": "54.218.4.189",
                "architecture": "x86_64",
                "rootDeviceType": "ebs",
                "rootDeviceName": "/dev/sda1",
                　　<中略>
            }
        }
    ]
}
```

> AWS Config
> https://aws.amazon.com/jp/config/

> AWS再入門 AWS Config編
> http://dev.classmethod.jp/cloud/aws/cm-advent-calendar-2015-aws-re-entering-aws-config/

> AWS Configを使ったAWS環境の見える化
> http://www.slideshare.net/morisshi/develipersio-2016-e1-aws-configaws

## AWS Config Partner について

　AWS Config Partnerに登録されている有料のサービスを活用することもできます。

> AWS Config Partners
> https://aws.amazon.com/config/partners/

> Logstorage連携パック for AWS Config
> http://www.logstorage.com/welcome/awsconfig_pack.html

> LogstorageでAWSの全体構成を可視化する
> http://dev.classmethod.jp/cloud/aws/aws-logstorage-config/

　ただ、有料のサービスのため、個人利用では気軽に試しにくいと思います。また、商用利用であっても、AWSサービス利用料以上の金額をその他の付加サービスにかけるのは抵抗があるケースも多いと思います。そのため、今回はD3.jsで可視化を試みます。

## AWS CLI について

AWS Configの対応サービスの制約等により、要件を満たせない場合は、AWS CLI（コマンドラインインターフェイス）から取得したAWS各種サービスの情報をjq（JSONパーサー）で加工することもできます。

> AWS コマンドラインインターフェイス
> https://aws.amazon.com/jp/cli/

> AWS Black Belt Tech シリーズ 2015 AWS CLI & AWS Tools for Windows Powershell
>  http://www.slideshare.net/AmazonWebServicesJapan/aws-black-belt-tech-2015-aws-cloudtrail-aws-sdk-for-powershell

> jq
> https://stedolan.github.io/jq/

> 軽量JSONパーサー『jq』のドキュメント：『jq Manual』をざっくり日本語訳してみました
> http://dev.classmethod.jp/tool/jq-manual-japanese-translation-roughly/
