---
title: Upozornění (úroveň 4) C4435 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a69e0d899e1a79c1d91b7c18c0eacaf66d32a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027294"
---
# <a name="compiler-warning-level-4-c4435"></a>Kompilátor upozornění (úroveň 4) C4435

'class1': z důvodu virtuální base 'class2' se změní rozložení objektů v /vd2

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

## <a name="see-also"></a>Viz také

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (zakázání přesunutí konstrukcí)](../../build/reference/vd-disable-construction-displacements.md)