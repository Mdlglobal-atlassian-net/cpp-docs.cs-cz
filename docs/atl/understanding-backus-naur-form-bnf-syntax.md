---
title: Registrátor ATL a syntaxe Backus-Naur Form (BNF)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168706"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Principy syntaxe Backus-Naurovy formy (BNF)

Skripty používané registrátorem ATL jsou popsány v tomto tématu pomocí syntaxe BNF, která používá zápis uvedený v následující tabulce.

|Konvence nebo symbol|Význam|
|------------------------|-------------|
|::=|Ekvivalent|
|&#124;|NEBO|
|X +|Jeden nebo více xs.|
|\[Znak|X je volitelné. Volitelné oddělovače jsou označeny znakem \[].|
|Libovolný **tučný** text|Řetězcový literál.|
|Libovolný text v *kurzívě*|Způsob konstrukce řetězcového literálu.|

Jak je uvedeno v předchozí tabulce, skripty registrátora používají řetězcové literály. Tyto hodnoty jsou skutečný text, který se musí objevit ve vašem skriptu. V následující tabulce jsou popsány řetězcové literály používané ve skriptu registrátora ATL.

|Řetězcový literál|Akce|
|--------------------|------------|
|**ForceRemove**|Zcela odebere další klíč (pokud existuje) a pak ho znovu vytvoří.|
|**Odebrat**|Neodebere další klíč během Odregistrace.|
|**počítává**|Určuje, `<Key Name>` že ve skutečnosti je pojmenovaná hodnota.|
|**Odstranit**|Odstraní další klíč během registrace.|
|**pracují**|Určuje, že další hodnota je řetězec (REG_SZ).|
|**trojrozměrné**|Určuje, že další hodnotou je DWORD (REG_DWORD).|
|**4m**|Určuje, že další hodnotou je Víceřetězcová hodnota (REG_MULTI_SZ).|
|**b**|Určuje, že další hodnota je binární hodnota (REG_BINARY).|

## <a name="bnf-syntax-examples"></a>Příklady syntaxe BNF

Tady je několik příkladů syntaxe, které vám pomohou pochopit, jak se literály řetězců zápisu a řetězce pracují ve skriptu ATL.

### <a name="syntax-example-1"></a>Příklad syntaxe 1

> \<výraz registru>:: = \<přidat klíčovou>

Určuje, `registry expression` že je ekvivalentní `Add Key`.

### <a name="syntax-example-2"></a>Příklad syntaxe 2

> \<výraz registru>:: = \<přidat klíčovou> | \<Odstranit> klíčů

Určuje, `registry expression` že je ekvivalentní buď `Add Key` nebo `Delete Key`.

### <a name="syntax-example-3"></a>Příklad syntaxe 3

> \<Název klíče>:: = '\<alfanumerické>+ '

Určuje, `Key Name` že je ekvivalentem jedné nebo `AlphaNumeric` více hodnot.

### <a name="syntax-example-4"></a>Příklad syntaxe 4

> \<Přidejte klíčovou>:: =**[ForceRemove** | **\ Remove** | **Val**]\<název klíče>

Určuje, `Add Key` že je ekvivalentní `Key Name`a že řetězcové literály, `ForceRemove`, `NoRemove`a `val`, jsou nepovinné.

### <a name="syntax-example-5"></a>Příklad syntaxe 5

> \<Alfanumerické>:: = *libovolný znak není null, to znamená ASCII 0*

Určuje, `AlphaNumeric` že je ekvivalentní libovolnému znaku, který není null.

### <a name="syntax-example-6"></a>Příklad syntaxe 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

Určuje, že název `testmulti` klíče je Víceřetězcová hodnota skládající se z `String 1` a. `String 2`

### <a name="syntax-example-7"></a>Příklad syntaxe 7

```rgs
val 'testhex' = d '&H55'
```

Určuje, že název `testhex` klíče je hodnota DWORD nastavená na šestnáctkovou hodnotu 55 (desítková 85). Všimněte si, že tento formát odpovídá notaci **&H** , jak se nachází ve specifikaci Visual Basic.

## <a name="see-also"></a>Viz také

[Vytváření skriptů registrátora](../atl/creating-registrar-scripts.md)
