# trx 波场钱包

### 生成私钥、公钥、地址

```go
package main

import (
	"encoding/hex"
	"fmt"
	"github.com/ijoywan/trx/wallet"
)

func main() {
	priv, pub := wallet.GenerateTrxKeys()
	fmt.Println("Private: ", hex.EncodeToString(priv))  // 私钥
	fmt.Println("Pub: ", hex.EncodeToString(pub)) //公钥
	b58Addr, hexAddr := wallet.PubToAddress(pub) 
	fmt.Println("B58Addr: ", b58Addr)  // 地址
	fmt.Println("HexAddr: ", hexAddr)

}

```

### 签名

```go
package main

import (
	"github.com/ijoywan/trx/sign"
)

func main() {
	privKey := "245e817e1d8cc348b40b366b22fb6070feb6dfd2ee441d13c193114f4987d45f"

	/*
		raw_data_hex: 通过wallet/createtransaction接口生成，详细http接口文档： https://github.com/tronprotocol/documentation/blob/master/TRX_CN/Tron-http.md
		privateKeyStr：16进制的私钥
	*/
	raw_data_hex := "0a028f8b22088b73d8d9386a59d340c0bcddb0e22d5a69080112650a2d747970652e676f6f676c65617069732e636f6d2f70726f746f636f6c2e5472616e73666572436f6e747261637412340a154106c6a577814bc4f1cf73057ada02a3a8e05f51481215417eb81b56a44ed4c13f3afbdc4c068bbf1b2b5d39189adbd6ee0170deeed9b0e22d"

	raw, err := TrxSignByPrivateStr(raw_data_hex ,privKey)
	}

	if err != nil {
		fatal(err)
	}
	println(raw)
}
```