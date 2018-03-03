---
title: __thiscall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a55f7d288758b345dfc4f182f2153e0d39a1b349
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="thiscall"></a>__thiscall
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__thiscall` Konvence volání se používá na členské funkce a konvence volání výchozí používané C++ členské funkce, které nepoužívají proměnné argumenty. V části `__thiscall`, volaného vyčistí zásobníku, což je znemožňuje, aby `vararg` funkce. Argumenty jsou vložena v zásobníku zprava doleva, se `this` ukazatel předávány prostřednictvím registrace ECX a ne v zásobníku, na x86 architektura.  
  
 Jedním z důvodů používat `__thiscall` v třídy, jejichž členské funkce použití `__clrcall` ve výchozím nastavení. V takovém případě můžete použít `__thiscall` , aby jednotlivými členy funkce volány z nativního kódu.  
  
 Při kompilaci s [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), jsou všechny funkce a ukazatelů na funkce `__clrcall` není uvedeno jinak. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Ve verzích před Visual C++ 2005 thiscall – konvence volání nelze zadat explicitně v programu, protože `thiscall` nebyla klíčové slovo.  
  
 `vararg`Členské funkce pomocí `__cdecl` konvence volání. Všechny argumenty funkce jsou vložena do zásobníku, se `this` v zásobníku poslední umístit ukazatel  
  
 Protože tato konvence volání se vztahuje pouze na C++, neexistuje žádné schéma decoration název C.  
  
 Na ARM a [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] počítače, `__thiscall` je přijatá a ignorovat kompilátoru.  
  
 U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)