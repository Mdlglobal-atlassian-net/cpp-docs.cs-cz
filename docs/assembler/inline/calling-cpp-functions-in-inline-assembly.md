---
title: Volání funkcí jazyka C++ ve vloženém sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbd8038d240bc2ab0240d172d914790b6ca02ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049620"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C++ v sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__asm` Bloku volat pouze globální C++ funkce, které nejsou přetížený. Při volání přetížené globální funkce C++ nebo členské funkce C++, vydá k chybě.  
  
 Můžete také volat jakékoli funkce deklarovat s **extern "C"** propojení. To umožňuje `__asm` bloku v rámci programu C++ pro volání funkcí knihovny jazyka C, protože všechny soubory standardní hlavičku deklarovat funkce knihovny tak, aby měl **extern "C"** propojení.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)