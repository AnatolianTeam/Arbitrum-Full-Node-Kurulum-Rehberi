# Arbitrum Full Node Kurulum Rehberi

![Arbitrum-GitHub](https://user-images.githubusercontent.com/102043225/225761437-c26bdf18-3feb-43e0-95a2-ee50efe36107.jpg)

## Gereksinimler 
| Bileşenler | Minimum Gereksinimler | **Tavsiye Edilen Gereksinimler** | 
| ------------ | ------------ | ------------ |
| CPU |	2 | 4 |
| RAM	| 4 GB | 8 GB |
| Storage	| 1.2 TB | 1.2+ TB |

## Arbitrum Dosyasının Oluşturulması ve İzinlerin Verilmesi
```
mkdir -p ~/data/arbitrum
chmod -fR 777 ~/data/arbitrum
```
## Docker Kurulumu
```
sudo apt install docker.io -y
```

## Arbitrum Kurulumu
:rotating_light: Aşağıda değiştirmeniz gereken yer belirtilmiştir.
* ALCHEMY_ETH_MAINNET_URL bu bölüme Alhcemy'den alacağınız url'yi yazacaksınız.
```
docker run -d -v ~/data/arbitrum:/home/user/.arbitrum -p 0.0.0.0:8547:8547 -p 0.0.0.0:8548:8548 offchainlabs/nitro-node:v2.0.11-8e786ec --l1.url ALCHEMY_ETH_MAINNET_URL --l2.chain-id=42161 --http.api=net,web3,eth,debug --http.corsdomain=* --http.addr=0.0.0.0 --http.vhosts=* --init.url="https://snapshot.arbitrum.io/mainnet/nitro.tar"
```

## Container UD Öğrenme
```
docker ps -a
```
Kodunuzun çıktısı aşağıdaki gibi olacak.
<img width="1080" alt="Ekran Resmi 2023-03-17 01 10 13" src="https://user-images.githubusercontent.com/102043225/225764013-caaaeea2-c09f-43a2-9ab4-4566dcf09d86.png">

## Snapshot'un Yüklenmesi ve Loglar
CONTAINER_ID bu bölüme id'nizi yazacaksınız.
```
docker logs --tail 100 CONTAINER_ID
```

## Screen İçerisinde Logları Görüntülemek İsterseniz

Eğer screen yüklü değilse kuralım.

```
apt install screen
```

Screen Oluşturalım
```
screen -S arb
```
Loglara bakalım
```
docker logs -f CONTAINER_ID
```

[Kaynak](https://developer.arbitrum.io/node-running/running-a-node)
