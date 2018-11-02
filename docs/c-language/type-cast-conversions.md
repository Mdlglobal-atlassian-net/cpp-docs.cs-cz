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
ms.openlocfilehash: d2de646d9ad3082c43ce896fdf4bc3c7e55a4405
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505297"
---
# <a name="type-cast-conversions"></a>Převody přetypování

Přetypování typu můžete použít k explicitnímu převodu typů.

**Syntaxe**

*výraz CAST*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Unární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *název typu*  **)**  *výrazem přetypování.*

*Název typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor qualifier-list* *abstraktní deklarátor*<sub>optimalizované</sub>

*Název typu* je typ a *výrazem přetypování* je hodnota má být převeden na typu. Výraz s přetypování není l hodnotou. *Výrazem přetypování* je převedena, jako by měl přiřazený k proměnné typu *název typu*. Pravidla převodu pro přiřazení (uvedených v [převody přiřazení](../c-language/assignment-conversions.md)) platí u typu přetypování také. V následující tabulce jsou uvedeny typy, které může být převeden do daného typu.

### <a name="legal-type-casts"></a>Právní přetypování

|Určení typů|Potenciální zdroje|
|-----------------------|-----------------------|
|Celočíselné typy|Libovolný celočíselný typ nebo typ s plovoucí desetinnou čárkou nebo ukazatel na objekt|
|S plovoucí desetinnou čárkou|Žádné aritmetický typ|
|Ukazatel na objekt, nebo (**void** <strong>\*</strong>)|Jakýkoli typ celé číslo (**void** <strong>\*</strong>), ukazatel na objekt nebo ukazatel na funkci|
|Ukazatel na funkci|Libovolný integrální typ, ukazatel na objekt nebo ukazatel na funkci|
|Struktury, sjednocení nebo pole|Žádné|
|Typ void.|Jakýkoli typ|

Žádný identifikátor lze převést na `void` typu. Nicméně, pokud typ zadaný v výraz přetypování není `void`, potom se identifikátor přetypovat na, že typ nemůže být `void` výrazu. Libovolný výraz může být převeden na `void`, ale výraz typu `void` nelze přetypovat na libovolného typu. Například funkce s `void` vrátit typ nemůže mít jeho návratový přetypován na jiný typ.

Všimněte si, že **void** <strong>\*</strong> má výraz typu ukazatele do `void`, nikoli na typ `void`. Pokud objekt je přetypován na `void` typ, výsledný výraz nelze přiřadit k libovolné položky. Podobně přetypování objektu není přijatelné l hodnotou, proto nelze realizovat žádná přiřazení k objektu přetypování.

**Specifické pro Microsoft**

Přetypování typu může být výraz l hodnotou, tak dlouho, dokud velikost identifikátor nezmění. Informace o výrazech l hodnotou, naleznete v tématu [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md).

**Specifické pro END Microsoft**

Můžete převést na typ výrazu `void` pomocí přetypování, ale výsledný výraz lze použít pouze pokud hodnota není povinné. Ukazatelem na objekt převést na **void** <strong>\*</strong> a vrátí zpět na původní typ na původní hodnotu.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)