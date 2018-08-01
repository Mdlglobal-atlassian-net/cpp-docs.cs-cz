---
title: Auto – klíčové slovo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a02ed2a19f44f19396038f8e41cb1c7f5a069407
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405883"
---
# <a name="auto-keyword"></a>auto – klíčové slovo
**Automaticky** – klíčové slovo je specifikátorem deklarace. Avšak standard jazyka C++ definuje původní a revidovaný význam tohoto klíčového slova. Před Visual C++ 2010 **automaticky** – klíčové slovo deklaruje proměnnou *automatické* třídy úložiště, což znamená, proměnná, která má místní dobu platnosti. Od verze Visual C++ 2010 **automaticky** – klíčové slovo deklaruje proměnnou, jejíž typ je odvozen z výrazu inicializace při deklaraci. [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru řídí význam **automaticky** – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Poznámky  
 Definice **automaticky** – klíčové slovo změny v programovacím jazyce C++, ale ne v programovacím jazyce C.  
  
 Následující témata popisují **automaticky** – klíčové slovo a odpovídající možnost kompilátoru:  
  
-   [Automatické](../cpp/auto-cpp.md) popisuje novou definici **automaticky** – klíčové slovo.  
  
-   [/ Zc: Auto (odvození typu proměnné)](../build/reference/zc-auto-deduce-variable-type.md) popisuje možnost kompilátoru sdělující kompilátoru, kterou definici **automaticky** – klíčové slovo použití.  
  
## <a name="see-also"></a>Viz také:  
 [Klíčová slova](../cpp/keywords-cpp.md)