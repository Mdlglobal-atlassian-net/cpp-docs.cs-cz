---
title: Kompilátor upozornění (úroveň 4) C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 43c13c484d6e9accee7c4d2c58b72a4539a75c4c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041225"
---
# <a name="compiler-warning-level-4-c4435"></a>Kompilátor upozornění (úroveň 4) C4435

'class1': Rozložení objektu pod: / vd2 se změní z důvodu virtuální base 'class2'

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Ve výchozí možnost/vd1 kompilace, odvozená třída nemá `vtordisp` pole pro uvedené virtuální základní třídy.  Pokud/vd2 nebo `#pragma vtordisp(2)` je v platnosti `vtordisp` pole bude k dispozici, změna rozložení objektů.  To může vést k problémům binární kompatibilitu, pokud komunikující moduly jsou kompilovány pomocí různých `vtordisp` nastavení.

## <a name="example"></a>Příklad

Následující ukázka generuje C4435.

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>Viz také:

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (zakázání přesunutí konstrukcí)](../../build/reference/vd-disable-construction-displacements.md)