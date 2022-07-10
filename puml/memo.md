
# About CreateCosmosProvider.puml
TODO
- [ ] 使用するkeyを設定する機能？

cosmos-sdk/crypto/keyring/keyring.go

デフォルトでetermint用のEthSecp256k1Optionを設定する？


これ見てる
/$HOME/go/pkg/mod/github.com/strangelove-ventures/lens@v0.5.1 /client/chain_client.go


```
func NewChainClient(log *zap.Logger, ccc *ChainClientConfig, homepath string, input io.Reader, output io.Writer, kro ...keyring.Option) (*ChainClient, error) {
	ccc.KeyDirectory = keysDir(homepath, ccc.ChainID)
	cc := &ChainClient{
		log: log,

		KeyringOptions: append([]keyring.Option{ethhd.EthSecp256k1Option()}, kro...),
		Config:         ccc,
		Input:          input,
		Output:         output,
		Codec:          MakeCodec(ccc.Modules),
	}
	if err := cc.Init(); err != nil {
		return nil, err
	}
	return cc, nil
}
```
