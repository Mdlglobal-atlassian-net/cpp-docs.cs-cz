---
title: Registrátor ATL a Backus-Naur syntaxe formuláře (BNF)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 77f0fa6fef8e517e5714d1da6c61d0e310e0718c
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65709160"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Principy syntaxe (BNF) formuláře Backus-Naur

Skripty používané Registrátor ATL jsou popsané v tomto tématu pomocí syntaxe BNF, který se používá zápis je znázorněno v následující tabulce.

|Konvence/symbol|Význam|
|------------------------|-------------|
|::=|Ekvivalent|
|&#124;|NEBO|
|X+|Nejmíň jeden Xs.|
|\[X]|X je volitelné. Volitelné oddělovače jsou rozlišeny pomocí \[].|
|Žádné **tučné** text|Řetězcový literál.|
|Žádné *kurzívou* text|Jak sestavit řetězcový literál.|

Jak je uvedeno v předchozí tabulce, používat skripty registrátora řetězcové literály. Tyto hodnoty jsou vlastní text, který musí být uvedena ve skriptu. Řetězcové literály, použít ve skriptu Registrátor ATL naleznete v následující tabulce.

|Řetězcový literál|Akce|
|--------------------|------------|
|**ForceRemove**|Úplně odebere další klíče (pokud existuje) a potom znovu vytvoří.|
|**NoRemove**|Další klíče při zrušení registrace neodebere.|
|**Val**|Určuje, že `<Key Name>` je ve skutečnosti pojmenovaná hodnota.|
|**Delete**|Odstraní Další klíč během registrace.|
|**s**|Určuje, že je hodnota dalšího řetězce (REG_SZ).|
|**d**|Určuje, že následující hodnotu DWORD (REG_DWORD).|
|**m**|Určuje, že je hodnota dalšího FixedLength multistring (REG_MULTI_SZ).|
|**b**|Určuje, že je hodnota dalšího binární hodnotu (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Příklady syntaxe BNF

Tady je pár příkladů syntaxe, které vám pomohou pochopit, jak fungují zápisu a řetězcovým literálům ve skriptu Registrátor ATL.

### <a name="syntax-example-1"></a>Příklad syntaxe 1

```
<registry expression> ::= <Add Key>
```

Určuje, že `registry expression` je ekvivalentní `Add Key`.

### <a name="syntax-example-2"></a>Příklad syntaxe 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

Určuje, že `registry expression` je ekvivalentem `Add Key` nebo `Delete Key`.

### <a name="syntax-example-3"></a>Příklad syntaxe 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

Určuje, že `Key Name` je ekvivalentní k jednomu nebo více `AlphaNumerics`.

### <a name="syntax-example-4"></a>Příklad syntaxe 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

Určuje, že `Add Key` je ekvivalentní `Key Name`a že řetězcové literály `ForceRemove`, `NoRemove`, a `val`, jsou volitelné.

### <a name="syntax-example-5"></a>Příklad syntaxe 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

Určuje, že `AlphaNumeric` je ekvivalentní k žádné jiné – znak NULL.

### <a name="syntax-example-6"></a>Příklad syntaxe 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

Určuje, že název klíče `testmulti` je nahrazován hodnotu složenou ze `String 1` a `String 2`.

### <a name="syntax-example-7"></a>Příklad syntaxe 7

```
val 'testhex' = d '&H55'
```

Určuje, že název klíče `testhex` je nastavena hodnotu DWORD hexadecimální 55 (desítková 85). Poznámka: Tento formát odpovídá **& H** notation jako součástí specifikace jazyka Visual Basic.

## <a name="see-also"></a>Viz také:

[Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)
