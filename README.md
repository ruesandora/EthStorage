# EthStorage

> Herhangi bi sunucunuzda bu işlemleri yapabilirsiniz sistem gereksinimleri önemsiz.
> 
> Yeni bir cüzdan oluşturun ve Sepolia test ağında Eth bulundurun. Eth priv keyinizi not defterine kaydedin lazım olacak. [Faucet link](https://www.alchemy.com/faucets/ethereum-sepolia)
>
## NodeJS ve Npm kuralım.
```
sudo apt-get update && sudo apt-get upgrade -y
apt install curl iptables build-essential git wget jq make gcc nano tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen -y
curl -sL https://deb.nodesource.com/setup_20.x -o /tmp/nodesource_setup.sh
sudo bash /tmp/nodesource_setup.sh
sudo apt install nodejs
npm install -g npm@10.4.0 
```

## Dosyaları oluşturalım
```
mkdir dist
cd dist
npm i -g ethfs-cli
wget https://raw.githubusercontent.com/enzifiri/GitHub-Achievements/main/degen.jpeg
nano app.html
```

> app.html içerisine Alttaki kodu yapıştırım

```
<html>
    <head>
        <script> 
            async function fetchData() { 
                // web3 URL is define in https://eips.ethereum.org/EIPS/eip-4804, please find more detail on https://web3url.io
                const url = 'web3://0xEDc9a588C4F6b223F6bff346A9e1923Ad2384804:11155111/greeting'; 
                const response = await fetch(url); 
                const data = await response.text(); 
                document.getElementById('content').textContent = data; 
            } 
            window.onload = fetchData; 
        </script>
    </head>
    <body>
        <div id="content"> Loading greeting... </div>
        <br>
        <img  src="./degen.jpeg"  alt="">	
    </body>	
</html>
```

## Kuruluma geçelim. 
> PRIVKEY kısmını değiştirmeyi unutma.
>
> Çıktıdaki FlatDirectory Addressi not defterine kaydedin. Bir sonraki kodda değiştireceksiniz
```
ethfs-cli create -p PRIVKEY -c 11155111
```

> ![image](https://github.com/ruesandora/EthStorage/assets/101149671/ad709fcc-5a1f-41f3-b4df-be5bf82224ef)


## dAPPi oluşturalım ETH ile
>  Flat directory ve priv key kısmını düzenlemeyi unutmayın
>
> Cüzdanınızda Sepolia ETH yoksa işlem hata verecektir. 0.05 yeter ve artar. Çıktıda Totalle başlayan bir şeyler görürseniz başarmışsınızdır.
```
ethfs-cli upload -f dist -a FLATDIRECTORYADRESS -c 11155111 -p PRIVKEY -t 1
```
> ![image](https://github.com/ruesandora/EthStorage/assets/101149671/1c15fb77-053b-473c-8f74-e99abdb9093d)

>

# Blob oluşturup dosyalarımızı kaydedelim.
> PRIVKEYINIZ ve CUZDANADRESINIZ kısımlarını düzenleyin. Eğer hata alıyorsanız farklı sepolia rpc deneyebilirsiniz.
```
cd
npm i -g eth-blob-uploader
eth-blob-uploader -r https://ethereum-sepolia-rpc.publicnode.com -p PRIVKEYINIZ -f dist/app.html -t CUZDANADRESINIZ
eth-blob-uploader -r https://ethereum-sepolia-rpc.publicnode.com -p PRIVKEYINIZ   -f dist/degen.jpeg -t CUZDANADRESINIZ
```
> Başarılı olursanız Mavi yazılı çıktılar verecektir. Sonraki adıma geçin.
>

# ETHStorage + Eth ile basit bir dAPP oluşturalım.
> Flatdirectory adresinizi 2. komuttaki yerde değiştirin
```
ethfs-cli create -p PRIVKEYINIZ -c 11155111
ethfs-cli upload -f dist -a FLATDIRECTORYADRESS -c 11155111 -p PRIVKEYINIZ -t 2
```
> Görseldeki çıktıyı alıyorsanız doğru yapmışsınızdır.

> ![image](https://github.com/ruesandora/EthStorage/assets/101149671/3262d8db-8d55-4c21-ad06-192bb7d1678c)



# Her şey tamamdır. Şimdi sitenizi kontrol edin. alttaki linki düzenleyin ve webte aratın. Formları doldurmayı unutmayın.
> En son oluşturduğunuz Flat adresinizle aratın.
```
https://FLATDIRECTORYADRESS.3333.w3link.io/app.html
```
> ![image](https://github.com/ruesandora/EthStorage/assets/101149671/1d3f99c5-475e-46e3-af55-6ff639cb2005)

# Form Linkleri 

> 1. Form  (Başvuru) https://dawme4mo.forms.app/ethstorage-2nd-campaign-application

>Alttaki metine cüzdan adresinizi girin ve twitterdan twit atın.
>
>Başvurunuz onaylanınca size Twitter üzerinden Mesaj atacaklar. Mesaj ayarlarınızın herkese açık oldugundan emin olun
>
>Test cüzdan adresinizi verin.
```
I am applying to participate in the EthStorage public testnet, and my miner address is <CUZDAN ADRESINIZ>
```

> 2. Form (Kanıt) https://dawme4mo.forms.app/ethstorage-2nd-campaign-submission
> 
> Bu sefer twitinize web3:// ile oluşturduğunuz linki de ekleyin.
```
my address: CÜZDAN ADRESINIZ FLATOLAN DEGIL
my dapp: web3://FLATCUZDANADRESS:3333/app.html
@EthStorage 
```
