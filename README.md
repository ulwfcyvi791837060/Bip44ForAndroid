# Bip44ForAndroid
Bip44 implementions for android.


[ ![Download](https://api.bintray.com/packages/loveit/maven/Bip44ForAndroid/images/download.svg) ](https://bintray.com/loveit/maven/Bip44ForAndroid/_latestVersion)



> # suppor Android sdk >= 14 #

**- Use it**


## code: ##

```java

                    //get 12 words
                    List<String> words = Bip44Utils.generateMnemonicWords(MainActivity.this);
                    Log.e("TAG", "words: " + words.toString());

                    // get bip39 seed
                    byte[] seed = Bip44Utils.getSeed(words);
                    Log.e("TAG", "seed: " + new BigInteger(1,seed).toString(16));

                    //get PrivateKey by path
                    BigInteger pri1 = Bip44Utils.getPathPrivateKey(words,"m/44'/194'/0'/0/0");
                    Log.e("TAG", "pri1: " + pri1.toString(16));

                    BigInteger pri2 = Bip44Utils.getPathPrivateKey(words,seed,"m/44'/194'/0'/0/0");
                    Log.e("TAG", "pri2: " + pri2.toString(16));

                    byte[] pri3 = Bip44Utils.getPathPrivateKeyBytes(words, "m/44'/194'/0'/0/0");
                    Log.e("TAG", "pri3: " + new BigInteger(1,pri3).toString(16));

                    byte[] pri4 = Bip44Utils.getPathPrivateKeyBytes(words, seed,"m/44'/194'/0'/0/0");
                    Log.e("TAG", "pri4: " + new BigInteger(1,pri4).toString(16));

                    byte[] pri5 = Bip44Utils.getDefaultPathPrivateKeyBytes(words, 194);
                    Log.e("TAG", "pri5: " + new BigInteger(1,pri5).toString(16));

                    //if you use bitcoinj library,you can generate bitcoin privatekey and public key and address like this:

                    BigInteger pribtc = Bip44Utils.getPathPrivateKey(words,"m/44'/0'/0'/0/0");

                    ECKey ecKey = ECKey.fromPrivate(pribtc);

	                String publicKey = ecKey.getPublicKeyAsHex();
	                String privateKey = ecKey.getPrivateKeyEncoded(networkParameters).toString();
	                String address = ecKey.toAddress(networkParameters).toString();


                    //if you use web3j library,you can generate bitcoin privatekey and public key and address like this:

					BigInteger prieth = Bip44Utils.getPathPrivateKey(words,"m/44'/60'/0'/0/0");

                    ECKeyPair ecKeyPair = ECKeyPair.create(prieth);

	                String publicKey = Numeric.toHexStringWithPrefix(ecKeyPair.getPublicKey());
	                String privateKey = Numeric.toHexStringWithPrefix(ecKeyPair.getPrivateKey());
	                String address = "0x" + Keys.getAddress(ecKeyPair);
                    


```



## result: ##

```java

words: [course, question, calm, west, basket, kitten, salmon, absorb, tool, ankle, mixed, endorse]

seed: c03f5488370482658066b96a803fcceac46b68181024a545d814344cbf7d9da9b478a20d0b95ebef268b7c24afd4540c59a4567146d45d2db891ca2576d409c7

pri1: 6ef7a396546d4fcf26865e54033ad48db858d19b5a08782014a652f4b5469037

pri2: 6ef7a396546d4fcf26865e54033ad48db858d19b5a08782014a652f4b5469037

pri3: 6ef7a396546d4fcf26865e54033ad48db858d19b5a08782014a652f4b5469037

pri4: 6ef7a396546d4fcf26865e54033ad48db858d19b5a08782014a652f4b5469037

pri5: 6ef7a396546d4fcf26865e54033ad48db858d19b5a08782014a652f4b5469037


```



 **- How to dependencies**
1. Maven

```base
<dependency>
  <groupId>party.loveit</groupId>
  <artifactId>bip44forandroidlibrary</artifactId>
  <version>1.0.7</version>
  <type>pom</type>
</dependency>
```
2. Gradle

```base
compile 'party.loveit:bip44forandroidlibrary:1.0.7'

or

implementation 'party.loveit:bip44forandroidlibrary:1.0.7'

```
3. Ivy

```base
<dependency org='party.loveit' name='bip44forandroidlibrary' rev='1.0.7'>
  <artifact name='bip44forandroidlibrary' ext='pom' ></artifact>
</dependency>
```


 **- coin_type link**


[https://github.com/satoshilabs/slips/blob/master/slip-0044.md](https://github.com/satoshilabs/slips/blob/master/slip-0044.md)







 **- License**

     Copyright 2018 52it.party
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
       http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
