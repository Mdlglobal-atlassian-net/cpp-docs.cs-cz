---
title: vtordisp – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: 3c676ab2bfee1b6cf3caff3ab456a4f23f2744c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216477"
---
# <a name="vtordisp-pragma"></a>vtordisp – direktiva pragma

**C++Konkrétní**

Řídí přidání skrytého `vtordisp` člena přemístění konstrukce nebo zničení.

## <a name="syntax"></a>Syntaxe

> **#pragma vtordisp (** [ **push,** ] *n* **)** \
> **#pragma vtordisp (pop)** \
> **#pragma vtordisp ()** \
> **#pragma vtordisp (**  | [ **push,** ] {**off** } **)**

### <a name="parameters"></a>Parametry

**replik**\
Posune aktuální `vtordisp` nastavení do interního zásobníku kompilátoru a nastaví nové `vtordisp` nastavení na *n*.  Není-li zadána hodnota *n* , `vtordisp` aktuální nastavení zůstane beze změny.

**výstrah**\
Odebere záznam nejvyšší úrovně z interního zásobníku kompilátoru a obnoví `vtordisp` nastavení na odebraný hodnotu.

*n*\
Určuje novou hodnotu pro `vtordisp` nastavení. Možné hodnoty jsou 0, 1 nebo 2, které `/vd0`odpovídají možnostem, `/vd1`a `/vd2` kompilátoru. Další informace naleznete v tématu [/VD (zakázání posunutí konstrukcí)](../build/reference/vd-disable-construction-displacements.md).

**pnete**\
`#pragma vtordisp(1)`Ekvivalent.

**zaokrouhl**\
`#pragma vtordisp(0)`Ekvivalent.

## <a name="remarks"></a>Poznámky

Direktiva pragma **vtordisp** se vztahuje pouze na kód, který používá virtuální základy. Přepisuje-li odvozená třída virtuální funkci, kterou třída dědí z virtuální základní třídy, a pokud konstruktor nebo destruktor odvozené základní třídy tuto funkci volá pomocí ukazatele na virtuální základní třídu, kompilátor může do tříd s virtuálními základy zavést dodatečná skrytá pole `vtordisp`.

Direktiva pragma **vtordisp** ovlivňuje rozložení tříd, které následují. Možnosti `/vd0`, `/vd1` a`/vd2` určují stejné chování pro kompletní moduly. Zadáním 0 nebo **vypnuto** potlačíte `vtordisp` skryté členy. Vypněte **vtordisp** jenom v případě, že není k dispozici možnost konstruktorů a destruktorů třídy volat virtuální funkce na objektu, na `this` který ukazuje ukazatel.

Zadáním hodnoty 1 nebo **on**ve výchozím nastavení povolíte `vtordisp` skryté členy tam, kde jsou nezbytné.

Zadáním 2 umožníte `vtordisp` skrytým členům všech virtuálních základů s virtuálními funkcemi.  `#pragma vtordisp(2)`může být nutné zajistit správný výkon **dynamic_cast** u částečně vytvořeného objektu. Další informace naleznete v tématu [Upozornění kompilátoru (úroveň 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md).

`#pragma vtordisp()`bez argumentů obnoví `vtordisp` nastavení na počáteční nastavení.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
