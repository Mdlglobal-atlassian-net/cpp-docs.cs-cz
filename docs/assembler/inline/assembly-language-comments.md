---
title: Komentáře jazyka sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169601"
---
# <a name="assembly-language-comments"></a>Komentáře jazyka sestavení

**Specifické pro společnost Microsoft**

Instrukce v bloku `__asm` můžou používat komentáře k jazykům sestavení:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Vzhledem k tomu, že se makra jazyka C rozbalí do jedné logické čáry, nepoužívejte v makrech komentáře k jazykům sestavení. (Viz [definování __asmch bloků jako maker v jazyce C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Blok `__asm` může také obsahovat komentáře ve stylu jazyka C; Další informace naleznete v tématu [using C nebo C++ in __asm Blocks](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
