---
title: Komentáře jazyka sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 048635a874db604f872b4fa87d72bd06d0455438
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050760"
---
# <a name="assembly-language-comments"></a>Komentáře jazyka sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Podle pokynů `__asm` blok komentáře jazyka sestavení můžete použít:  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 Protože maker v jazyce C rozšířit do jedné logické řádky, nepoužívejte komentáře jazyka sestavení v makrech. (Viz [definování bloků __asm jako maker v jazyce C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) `__asm` Bloku může také obsahovat komentáře stylu jazyka C; Další informace najdete v tématu [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)