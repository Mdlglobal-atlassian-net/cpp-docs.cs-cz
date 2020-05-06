---
title: Převody přetypování
ms.date: 11/04/2016
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
ms.openlocfilehash: d54e4c15f84ccecad629d48341e5d3ae26d8cecf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344938"
---
# <a name="type-cast-conversions"></a>Převody přetypování

Můžete použít přetypování typů pro explicitní převod typů.

**Syntaktick**

*výraz cast*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *název typu*  **)**  *přetypování – výraz*

*název typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor – kvalifikátor – seznam* *Abstrakt-deklarátor –*<sub>výslovný souhlas</sub>

*Typ-Name* je typ a *přetypování-výraz* je hodnota, která má být převedena na tento typ. Výraz s přetypováním typu není l-hodnotou. *Výraz cast-expression* je převeden, jako by byl přiřazen proměnné typu Type *-Name*. Pravidla převodu pro přiřazení (popsaný v části [převody přiřazení](../c-language/assignment-conversions.md)) platí i pro přetypování typu. V následující tabulce jsou uvedeny typy, které lze přetypovat na libovolný daný typ.

### <a name="legal-type-casts"></a>Přetypování typu Legal

|Typy cílů|Potenciální zdroje|
|-----------------------|-----------------------|
|Celočíselné typy|Libovolný celočíselný typ nebo typ s plovoucí desetinnou čárkou nebo ukazatel na objekt|
|Plovoucí desetinná čárka|Jakýkoli aritmetický typ|
|Ukazatel na objekt nebo (**void** <strong>\*</strong>)|Libovolný celočíselný typ, (**void** <strong>\*</strong>), ukazatel na objekt nebo ukazatel na funkci|
|Ukazatel na funkci|Libovolný celočíselný typ, ukazatel na objekt nebo ukazatel na funkci|
|Struktura, sjednocení nebo pole|Žádné|
|Typ void|Libovolný typ|

Libovolný identifikátor lze přetypovat na `void` typ. Nicméně pokud typ určený ve výrazu přetypování není v typu `void`, pak identifikátor, který je převeden na tento typ, nemůže být `void` výraz. Libovolný výraz lze přetypovat na `void`, ale výraz typu `void` nelze přetypovat na jiný typ. Například funkce s `void` návratovým typem nemůže mít přetypování zpět na jiný typ.

Všimněte si, že výraz **void** <strong>\*</strong> má ukazatel typu na `void`typ, nikoli `void`na typ. Pokud je objekt přetypování na `void` typ, výsledný výraz nelze přiřadit žádné položce. Podobně objekt přetypování typu není přijatelná l-hodnota, takže nelze provést žádné přiřazení k objektu přetypování.

**Specifické pro Microsoft**

Přetypování typu může být výraz l-hodnoty, pokud se velikost identifikátoru nezmění. Informace o výrazech l-value naleznete v tématu [výrazy l-value a R-Value](../c-language/l-value-and-r-value-expressions.md).

**Specifické pro konec Microsoftu**

Můžete převést výraz na typ `void` s přetypování, ale výsledný výraz lze použít pouze tam, kde není požadována hodnota. Ukazatel na objekt převedený na **void** <strong>\*</strong> a zpátky na původní typ se vrátí na původní hodnotu.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)
