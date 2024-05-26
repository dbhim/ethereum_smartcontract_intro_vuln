[https://github.com/dbhim/ethereum_smartcontract_intro_vuln](https://github.com/dbhim/ethereum_smartcontract_intro_vuln)  
[https://gitverse.ru/dbhim/ethereum_smartcontract_intro_vuln](https://gitverse.ru/dbhim/ethereum_smartcontract_intro_vuln)

Представленные здесь учебные контракты содержат уязвимости, позволяющие стороннему атакующему (не владельцу контракта) получить все деньги с контракта. Это практическая часть [небольшого вводного курса по смартконтрактам](../ethereum_smartcontract_intro).

В качестве владельца атакуемых контрактов выступает контракт фабрики `VulnFactory`, который находится по адресу `0x5A1b4c66b7cdC2655A9E62807043A4905C2cc3C4`. Для получения собственной копии уязвимого контракта для взлома необходимо обратиться к соответствующей функции контракта фабрики, которая задеплоит контракт и вернёт его адрес. В функцию деплоя необходимо передать некоторое количество эфира. Этот эфир контракт фабрики передаст в задеплоенный контракт. Эти деньги и необходимо будет забрать атакующему в процессе эксплуатации.

Контракт фабрики развёрнут в публичной сети Polygon Amoy, ChainId 80002(0x13882). В MetaMask её можно подключить по ссылке [https://chainlist.org/chain/80002](https://chainlist.org/chain/80002).

Тестовые токены (MATIC) для этой сети можно получить по адресу [https://faucet.polygon.technology/](https://faucet.polygon.technology/) (выбрать сеть "Polygon Pos (Amoy)"). Требуется подписаться на их канал в дискорде. Транзакции в сети дешёвые, поэтому должно хватить надолго. Следует только при подтверждении транзакции в MetaMask выставлять самую минимальную цену (можно выбрать в пункте "Estimated fee").

Web-интерфейс к контракту фабрики доступен по адресу [https://dbhim.github.io/ethereum_smartcontract_intro_vuln/web](https://dbhim.github.io/ethereum_smartcontract_intro_vuln/web). На этой странице надо нажать кнопку подключения к кошельку MetaMask. После чего можно нажимать соответствующие кнопки деплоя контрактов. MetaMask запросит подтверждения транзакции и (в случае успешной транзакции) на странице отобразится адрес задеплоенного контракта. Web-интерфейс не сохраняет никакого состояния, поэтому при обновлении страницы надо повторять всё заново.

Рекомендуемый порядок действий
1. Настроить Remix на тестовую локальную сеть hardhat.
2. В локальной сети через Remix задеплоить контракт фабрики.
3. Через Remix вызовом соответствующего метода контракта фабрики задеплоить нужный уязвимый контракт в локальную сеть.
4. Найти уязвимость, написать контракт эксплоита, задеплоить его через Remix в локальную сеть и проэксплуатировать. Тем самым получив рабочий эксплоит.
5. Через web-интерфейс задеплоить уязвимый контракт в публичную сеть и получить его адрес.
6. Настроить Remix на публичную сеть через MetaMask (Remix может выводить сообщения, что не поддерживает эту сеть, но всё равно будет работать).
7. Добавить в Remix уязвимый контракт по его адресу (на вкладке "Deploy & run transactions" есть кнопка "At Address"), убедиться, что на его счёте есть деньги.
8. В Remix через MetaMask задеплоить контракт эксплоита в публичную сеть и проэксплуатировать уязвимость, забрав все деньги с контракта (через контракт эксплоита перевести на счёт атакующего).

Для тестирования есть простой уязвимый контракт `Vuln0` и эксплоит к нему `Exploit0`.