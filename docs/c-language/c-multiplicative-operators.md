---
title: Multiplikativní operátory jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: f9f5f62e2326826e3087a8668cd9107da4b85388
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335001"
---
# <a name="c-multiplicative-operators"></a>Multiplikativní operátory jazyka C

Multiplikativní operátory provádějí násobení (<strong>\*</strong>), dělení (**/**) a zbytek (**%**) operací.

## <a name="syntax"></a>Syntaxe

*multiplikativní-Expression*: &nbsp; &nbsp; &nbsp; &nbsp; *cast-expression* &nbsp; &nbsp; &nbsp; &nbsp; *cast-expression* **%** *multiplicative-expression* &nbsp; &nbsp; *multiplicative-expression* *cast-expression* &nbsp; &nbsp; *multiplicative-expression* *cast-expression* multiplikativní- <strong>\*</strong> Expression cast-Expression &nbsp;multiplikativní **/** -Expression Cast &nbsp;-Expression multiplikativní-Expression cast-Expression &nbsp; &nbsp;

Operandy operátoru zbytek (**%**) musí být integrální. Operátory násobení (<strong>\*</strong>) a dělení (**/**) mohou přijímat operandy typu integrál nebo float; typy operandů můžou být odlišné.

Multiplikativní operátory provádějí obvyklé aritmetické převody na operandech. Typ výsledku je typ operandů po převodu.

> [!NOTE]
> Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.

Multiplikativní operátory jazyka C jsou popsány níže:

|Operátor|Popis|
|--------------|-----------------|
|<strong>\*</strong>|Operátor násobení způsobí, že se vynásobí jeho dva operandy.|
|**/**|Operátor dělení způsobí, že první operand bude dělen druhým. Pokud jsou rozděleny dva celočíselné operandy a výsledek není celé číslo, zkrátí se na základě následujících pravidel:<br/><br/>-Výsledek dělení 0 není definován v souladu se standardem ANSI C. Kompilátor jazyka Microsoft C generuje chybu v době kompilace nebo v době běhu.<br/><br/>– Pokud jsou oba operandy kladné nebo bez znaménka, výsledek je zkrácen směrem k 0.<br/><br/>– Pokud je jeden operand záporný, zda je výsledkem operace největší celé číslo menší nebo rovno podílu algebraických, nebo je nejmenší celé číslo větší nebo rovno podílu algebraických, je definována implementace. (Další informace najdete v části specifické pro společnost Microsoft.)|
|**%**|Výsledek zbývajícího operátoru je zbytek při dělení prvního operandu druhým. Je-li dělení nepřesné, výsledek je stanoven pomocí následujících pravidel:<br/><br/>– Pokud je pravý operand nula, výsledek není definován.<br/><br/>– Pokud jsou oba operandy kladné nebo bez znaménka, výsledek je kladný.<br/><br/>– Pokud je jeden operand záporný a výsledek je nepřesný, je výsledkem definovaná implementace. (Další informace najdete v části specifické pro společnost Microsoft.)|

### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

V části dělení, kde je jeden operand záporný, je směr zkrácení směrem k 0.

Pokud je jedna operace v dělení s operátorem zbytek záporná, výsledek má stejné znaménko jako dividenda (první operand ve výrazu).

## <a name="examples"></a>Příklady

Níže uvedené deklarace jsou použity v následujících příkladech:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Tento příkaz používá operátor násobení:

```
y = x * i;
```

V tomto případě se `x` vynásobí, `i` aby se dala hodnota 20,0. Výsledek má typ **Double** .

```
n = i / j;
```

V tomto příkladu je 10 rozdělen podle 3. Výsledek je zkrácen směrem k 0, přičemž je výsledkem celočíselná hodnota 3.

```
n = i % j;
```

Tento příkaz přiřadí `n` celočíselný zbytek, 1, pokud je hodnota 10 dělena 3.

**Specifické pro Microsoft**

Znaménko zbytku je stejné jako znaménko dividendy. Příklad:

```
50 % -6 = 2
-50 % 6 = -2
```

V každém případě `50` a `2` mít stejné znaménko.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Multiplikativní operátory a operátor zbytku](../cpp/multiplicative-operators-and-the-modulus-operator.md)
