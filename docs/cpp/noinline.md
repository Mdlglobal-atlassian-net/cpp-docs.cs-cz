---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 6e424846c46dd50852b62008c4f1f38827da849c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857408"
---
# <a name="noinline"></a>noinline

**Specifické pro společnost Microsoft**

**__declspec (inline)** instruuje kompilátor, aby nikdy nevložený konkrétní členskou funkci (funkce ve třídě).

Nevkládání funkce může být výhodné, je-li malé a není-li důležité pro výkon kódu. To znamená, je-li funkce malá a nebude volána často, například funkce, která zpracovává chybovou podmínku.

Mějte na paměti, že pokud je funkce označená jako **inline**, volání funkce bude menší a bude tedy kandidátem pro vkládání kompilátoru.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[inline, __inline \__forceinline](inline-functions-cpp.md)
