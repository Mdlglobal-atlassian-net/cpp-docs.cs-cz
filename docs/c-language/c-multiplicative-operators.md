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

Multiplikativní operátory provádějí<strong>\*</strong>operace**/** násobení (**%**), dělení ( ) a zbytku ( ).

## <a name="syntax"></a>Syntaxe

*multiplikativní* &nbsp; &nbsp; &nbsp; &nbsp;výraz : *multiplicative-expression* **%** *cast-expression* *cast-expression* &nbsp; &nbsp; &nbsp; &nbsp; *multiplikativní* <strong>\*</strong> *výraz* &nbsp; &nbsp; &nbsp; &nbsp;přetypování a &nbsp; &nbsp; &nbsp; &nbsp; *výraz přetypování* *multiplicative-expression* **/**

Operandy operátoru zbytku**%**( ) musí být integrální. Násobilky<strong>\*</strong>( )**/** a dělení ( ) operátory mohou mít operandy integrálního nebo plovoucího typu; typy operandů se mohou lišit.

Multiplikativní operátory provádět obvyklé aritmetické převody na operandy. Typ výsledku je typ operandů po převodu.

> [!NOTE]
> Vzhledem k tomu, že převody prováděné operátory násobení nepočítají s podmínkami přetečení nebo podtečení, informace se mohou ztratit, pokud výsledek operace násobení nelze reprezentovat v typu operandu po převodu.

Multiplikativní operátory C jsou popsány níže:

|Operátor|Popis|
|--------------|-----------------|
|<strong>\*</strong>|Operátor násobení způsobí, že jeho dva operandy násobí.|
|**/**|Operátor dělení způsobí, že první operand, které mají být rozděleny podle druhého. Pokud jsou rozděleny dva celé operandy a výsledek není celé číslo, je zkrácen podle následujících pravidel:<br/><br/>- Výsledek dělení 0 není definován podle standardu ANSI C. Kompilátor Microsoft C generuje chybu v době kompilace nebo běhu.<br/><br/>- Pokud jsou oba operandy kladné nebo nepodepsané, výsledek je zkrácen směrem k 0.<br/><br/>- Je-li buď operand záporný, je definováno, zda je výsledkem operace největší celé číslo menší nebo rovno algebraickému kvocientu nebo je nejmenší celé číslo větší nebo rovné algebraickému kvocientu. (Viz část microsoft-specific níže.)|
|**%**|Výsledkem operátoru zbytek je zbytek při první operand je děleno druhý. Pokud je dělení nepřesné, výsledek je určen následujícími pravidly:<br/><br/>- Pokud je pravý operand nula, výsledek není definován.<br/><br/>- Pokud jsou oba operandy kladné nebo nepodepsané, výsledek je kladný.<br/><br/>- Pokud je buď operand záporný a výsledek je nepřesný, výsledek je definován implementací. (Viz část microsoft-specific níže.)|

### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

V dělení, kde je buď operand negativní, je směr zkrácení směrem k 0.

Pokud je některá z operací záporná v dělení s operátorem zbytku, výsledek má stejné znaménko jako dividenda (první operand ve výrazu).

## <a name="examples"></a>Příklady

Níže uvedená prohlášení se používají pro následující příklady:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Tento příkaz používá operátor násobení:

```
y = x * i;
```

V tomto `x` případě se `i` vynásobí, aby hodnota 20.0. Výsledek má **dvojitý** typ.

```
n = i / j;
```

V tomto příkladu je 10 děleno 3. Výsledek je zkrácen směrem k 0, čímž se vyloží celá hodnota 3.

```
n = i % j;
```

Tento příkaz `n` přiřadí celý zůstatek, 1, když 10 je děleno 3.

**Specifické pro Microsoft**

Znaménko zbytku je stejné jako znaménko dividendy. Příklad:

```
50 % -6 = 2
-50 % 6 = -2
```

V každém `50` případě, a `2` mají stejné znamení.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Multiplikativní operátory a operátor modulu](../cpp/multiplicative-operators-and-the-modulus-operator.md)
