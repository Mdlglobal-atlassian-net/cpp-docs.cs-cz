---
title: Komentáře jazyka sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578634"
---
# <a name="assembly-language-comments"></a>Komentáře jazyka sestavení

**Specifické pro Microsoft**

Podle pokynů `__asm` komentáře jazyka sestavení lze použít blok:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Vzhledem k tomu, že rozšíření maker v jazyce C do jednoho logického řádku, vyhněte se použití komentáře jazyka sestavení v makra. (Viz [definování bloků __asm jako maker v jazyce C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) `__asm` Bloku může taky obsahovat komentáře, C-style; Další informace najdete v tématu [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>