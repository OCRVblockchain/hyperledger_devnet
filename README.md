# hyperledger_devnet

Hyperledger devnet из одного пира и одного ордера, для разработки и тестирования технологии блокчейн.

## Перед началом убедитесь что установлен докер.

## Запуск

переходим в каталог с репозиторием
```
cd $HOME/hyperledger_devnet
```
Теперь запускаем команду:
```
docker-compose up -d
```
после успешного запуска контейнера вводим команду инициализации генезис файла:
После успешного старта, нам требуется создать канал:
```
docker exec -e "CORE_PEER_LOCALMSPID=Org1MSP" -e "CORE_PEER_MSPCONFIGPATH=/etc/hyperledger/msp/users/Admin@org1.example.com/msp" peer0.org1.example.com peer channel create -o orderer.example.com:7050 -c mychannel -f /etc/hyperledger/configtx/channel.tx
```
Далее пир нужно ввести в канал:
```
docker exec -e "CORE_PEER_LOCALMSPID=Org1MSP" -e "CORE_PEER_MSPCONFIGPATH=/etc/hyperledger/msp/users/Admin@org1.example.com/msp" peer0.org1.example.com peer channel join -b mychannel.block
```
Сеть развернута с одним ордером и с одним пиром.


## Для того чтобы остановить

выполняем команду

```
docker-compose down
```



