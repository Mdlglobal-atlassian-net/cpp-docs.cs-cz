---
title: Pravidla a omezení pro holé funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb18f3e75bb7d912cbafbde01893d6283a4c61f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="rules-and-limitations-for-naked-functions"></a>Pravidla a omezení pro holé funkce
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Na neviditelné funkce se vztahují následující pravidla a omezení:  
  
-   Příkaz `return` není povolen.  
  
-   Konstrukce strukturovaného zpracování výjimek a zpracování výjimek jazyka C++ nejsou povoleny, protože se musejí odvíjet prostřednictvím rámce zásobníku.  
  
-   Ze stejného důvodu je zakázána jakákoli forma `setjmp`.  
  
-   Použití funkce `_alloca` je zakázáno.  
  
-   Pro ujištění, že se před sekvencí prologu neobjeví žádná inicializace kódu lokálních proměnných, nejsou v rámci oboru funkce povoleny inicializované místní proměnné. Konkrétně není v oboru funkce povolena deklarace objektů jazyka C++. Ve vnořeném oboru se však mohou vyskytovat inicializovaná data.  
  
-   Optimalizace ukazatele rámce (možnost kompilátoru /Oy) se nedoporučuje, ale je u neviditelné funkce automaticky potlačena.  
  
-   V rámci oboru lexikální funkce nelze deklarovat třídu objektů jazyka C++. Objekty lze však deklarovat ve vnořeném bloku.  
  
-   `naked` – Klíčové slovo je ignorován, když kompilujete s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Pro [__fastcall](../cpp/fastcall.md) holé funkce vždy, když je v kódu C/C++ do jednoho z argumentů registru odkaz, kód prologu měli uložit hodnoty tohoto registru do zásobníku umístění pro tuto proměnnou. Příklad:  
  
```  
// nkdfastcl.cpp  
// compile with: /c  
// processor: x86  
__declspec(naked) int __fastcall  power(int i, int j) {  
   // calculates i^j, assumes that j >= 0  
  
   // prolog  
   __asm {  
      push ebp  
      mov ebp, esp  
      sub esp, __LOCAL_SIZE  
     // store ECX and EDX into stack locations allocated for i and j  
     mov i, ecx  
     mov j, edx  
   }  
  
   {  
      int k = 1;   // return value  
      while (j-- > 0)   
         k *= i;  
      __asm {   
         mov eax, k   
      };  
   }  
  
   // epilog  
   __asm {  
      mov esp, ebp  
      pop ebp  
      ret  
   }  
}  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Volání holé funkce](../cpp/naked-function-calls.md)