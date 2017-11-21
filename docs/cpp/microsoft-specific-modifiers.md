---
title: "Modifikátory specifické pro společnost Microsoft | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b1c98af83f4da73b437a1308e260b19024728b13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="microsoft-specific-modifiers"></a>Modifikátory specifické pro společnost Microsoft
Tato část popisuje specifické pro společnost Microsoft rozšíření pro C++ v těchto oblastech:  
  
-   [Základní adresování](../cpp/based-addressing.md), postup používání ukazatel jako základ, ze kterého lze posunout jiné ukazatele  
  
-   [Funkce konvence volání](../cpp/calling-conventions.md)  
  
-   Rozšířené atributy třídy úložiště deklarovat s [__declspec](../cpp/declspec.md) – klíčové slovo  
  
-   [__W64](../cpp/w64.md) – klíčové slovo  
  
 Řadu klíčová slova specifická pro společnost Microsoft může sloužit ke změně deklarátory na formulář odvozené typy. Další informace o deklarátorech najdete v tématu [Deklarátory](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
### <a name="microsoft-specific-keywords"></a>Klíčová slova specifická pro společnost Microsoft  
  
|– Klíčové slovo|Význam|Použít k vytvoření odvozené typy?|  
|-------------|-------------|---------------------------------|  
|[__based –](../cpp/based-grammar.md)|Název, který následuje deklaruje 32-bit posun základní 32-bit obsažené v deklaraci.|Ano|  
|[__cdecl](../cpp/cdecl.md)|Název, který následuje používá C pojmenování a konvence volání.|Ano|  
|[__declspec](../cpp/declspec.md)|Název, který následuje Určuje atribut třídy úložiště specifické pro společnost Microsoft.|Ne|  
|[__fastcall](../cpp/fastcall.md)|Název, který následuje deklaruje funkci, která používá registrů, pokud je k dispozici, místo zásobníku pro předávání argumentů.|Ano|  
|[__restrict](../cpp/extension-restrict.md)|Podobně jako __declspec ([omezit](../cpp/restrict.md)), ale pro použití v proměnné.|Ne|  
|[__stdcall](../cpp/stdcall.md)|Název, který následuje určuje funkce, které dodržuje standard konvence volání.|Ano|  
|[__w64](../cpp/w64.md)|Označí datový typ jako větší na 64-bit kompilátoru.|Ne|  
|[__unaligned](../cpp/unaligned.md)|Určuje, že není zarovnána ukazatel na určitý typ nebo jiná data...|Ne|  
|[__vectorcall](../cpp/vectorcall.md)|Název, který následuje deklaruje funkci, která používá registry, včetně SSE registrů, pokud je k dispozici místo v zásobníku pro předávání argumentů.|Ano|  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)