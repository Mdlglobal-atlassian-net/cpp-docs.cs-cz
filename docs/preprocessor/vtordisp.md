---
title: vtordisp
ms.date: 10/18/2018
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 075f00ad8a4071af57014638707503847b58756d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557180"
---
# <a name="vtordisp"></a>vtordisp

**Specifické pro C++**

Řídí přidání skrytého členu vtordisp pro přesunutí vytvoření nebo zničení.

## <a name="syntax"></a>Syntaxe

```cpp
#pragma vtordisp([push,] n)
#pragma vtordisp(pop)
#pragma vtordisp()
#pragma vtordisp([push,] {on | off})
```

### <a name="parameters"></a>Parametry

*push*<br/>
Posune aktuální nastavení vtordisp na vnitřního zásobníku kompilátoru a nastaví nové nastavení vtordisp na *n*.  Pokud *n* není zadán, aktuální nastavení vtordisp není změněno.

*POP*<br/>
Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru a obnoví nastavení vtordisp na odstraněnou hodnotu.

*n*<br/>
Určuje novou hodnotu nastavení vtordisp. Možné hodnoty jsou 0, 1 nebo 2, které `/vd0`, `/vd1`, a `/vd2` – možnosti kompilátoru. Další informace najdete v tématu [/vd (zakázat posunutí konstrukcí)](../build/reference/vd-disable-construction-displacements.md).

*on*<br/>
Ekvivalentní `#pragma vtordisp(1)`.

*Vypnout*<br/>
Ekvivalentní `#pragma vtordisp(0)`.

## <a name="remarks"></a>Poznámky

**Vtordisp** – Direktiva pragma se vztahuje pouze na kód, který používá virtuální základy. Pokud přepíše odvozená třída virtuální funkci, která dědí z virtuální základní třídy, a pokud konstruktor nebo destruktor odvozené třídě volá tuto funkci pomocí ukazatele na virtuální základní třídu, kompilátor může způsobit další skryté **vtordisp** pole do tříd s virtuálními základy.

**Vtordisp** – Direktiva pragma ovlivňuje rozložení tříd uvedených za ní. `/vd0`, `/vd1`, A `/vd2` možnosti zadat stejné chování pro kompletní moduly. Zadáním 0 nebo *vypnout* potlačí skrytého **vtordisp** členy. Vypnout **vtordisp** pouze pokud je nemohly žádným způsobem, který konstruktory a destruktory třídy volaly virtuální funkce objektu, na které odkazují **to** ukazatele.

Určení 1 nebo *na*, standardně povoleno použití skrytých **vtordisp** členy, kde jsou zapotřebí.

Určení 2 povoleno použití skrytých **vtordisp** členů pro všechny virtuální základy s virtuálními funkcemi.  `vtordisp(2)` může být nezbytné pro zajištění správné činnosti **dynamic_cast** na částečně vytvořeným objektem. Další informace najdete v tématu [upozornění kompilátoru (úroveň 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

Direktiva `#pragma vtordisp()` bez argumentů obnoví nastavení vtordisp na počáteční nastavení.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)