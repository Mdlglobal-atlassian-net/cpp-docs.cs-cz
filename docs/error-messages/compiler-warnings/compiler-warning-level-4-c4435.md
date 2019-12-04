---
title: Upozornění kompilátoru (úroveň 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 0ff545d3de3ef173cdbfd99d7714890e8631ce7a
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810671"
---
# <a name="compiler-warning-level-4-c4435"></a>Upozornění kompilátoru (úroveň 4) C4435

'class1': z důvodu virtuální base 'class2' se změní rozložení objektů v /vd2

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

V rámci výchozí možnosti kompilace/vd1 odvozená třída neobsahuje pole `vtordisp` pro uvedenou virtuální základnu.  Pokud je/VD2 nebo `#pragma vtordisp(2)`, bude k dispozici `vtordisp` pole, ve kterém se změní rozložení objektu.  To může vést k potížím s binární kompatibilitou, pokud jsou interaktivní moduly kompilovány s různými nastaveními `vtordisp`.

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