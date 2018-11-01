---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 3a8dce21aa707a1a52c647c9efee5ab806511ca8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454558"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Specifické pro Microsoft

**__declspec(noinline)** instruuje kompilátor, aby nikdy nevkládal členské funkce (funkce ve třídě).

Nevkládání funkce může být výhodné, je-li malé a není-li důležité pro výkon kódu. To znamená, je-li funkce malá a nebude volána často, například funkce, která zpracovává chybovou podmínku.

Mějte na paměti, která pokud je funkce označena **noinline**, volání funkce bude menší a proto samotné kandidátem pro vkládání kompilátoru.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)

