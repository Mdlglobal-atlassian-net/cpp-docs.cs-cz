---
title: Auto – klíčové slovo | Microsoft Docs
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
ms.openlocfilehash: 93b2f5e28dc0306a996b4c8bdb799122fe4646ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="auto-keyword"></a>auto – klíčové slovo
Klíčové slovo `auto` je specifikátorem deklarace. Avšak standard jazyka C++ definuje původní a revidovaný význam tohoto klíčového slova. Před Visual C++ 2010 `auto` – klíčové slovo deklaruje proměnnou v *automatické* třídy úložiště; to znamená, proměnné, která má místní životnost. Od verze Visual C++ 2010 `auto` – klíčové slovo deklaruje proměnnou, jejichž typ je odvozen z inicializace výrazu v jeho deklaraci. [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru ovládací prvky význam `auto` – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Poznámky  
 Definice klíčového slova `auto` se změnila v programovacím jazyce C++, ale ne v programovacím jazyce C.  
  
 Následující témata popisují klíčové slovo `auto` a odpovídající možnost kompilátoru:  
  
-   [Automatické](../cpp/auto-cpp.md) popisuje nové definice `auto` – klíčové slovo.  
  
  
-   [/ Zc: Auto (odvození typu proměnné)](../build/reference/zc-auto-deduce-variable-type.md) popisuje možnosti kompilátoru, která sděluje kompilátoru, která definice `auto` – klíčové slovo používat.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)