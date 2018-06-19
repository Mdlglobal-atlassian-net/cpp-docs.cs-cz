---
title: Konvence předávání a pojmenování argumentů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43aa3430b641f6333c6c35d618f9e9de123b7390
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413483"
---
# <a name="argument-passing-and-naming-conventions"></a>Konvence předávání a pojmenování argumentů
**Konkrétní Microsoft**  
  
 Kompilátory jazyka Visual C++ umožňují zadat konvence pro předání argumentů a návratové hodnoty mezi funkcemi a volající. Ne všechny konvence jsou dostupné na všech podporovaných platformách a některé konvence použít implementace specifické pro platformu. Ve většině případů klíčová slova nebo přepínače kompilátoru, která nepodporované konvence na konkrétní platformu, jsou ignorovány a používá výchozí konvenci platformy.  
  
 Na x86 plaftorms, všechny argumenty jsou rozšířit na 32 bitů, když jsou předávány. Návratové hodnoty jsou také rozšířit na 32 bitů a vrátí EAX registrace, s výjimkou struktury 8 bajtů, které jsou následně vráceny ve dvojici registrace EDX:EAX. Větší struktury se vrátí v registru EAX jako ukazatele na skrytá vrátit struktury. Parametry jsou vloženy do zásobníku zprava doleva. Struktury, které nejsou pracovními stanicemi soustředěnými kolem nejsou k dispozici v registrech.  
  
 Kompilátor generuje prologu a zaregistruje Kód epilogu k uložení a obnovení ESI, EDI, EBX a EBP, pokud se používají ve funkci.  
  
> [!NOTE]
>  Pokud struktury, sjednocení nebo třída se vrátí z funkce hodnotou, všechny definice typu musí být stejné, jinak se pravděpodobně nezdaří program za běhu.  
  
 Informace o tom, jak definovat vlastní kód prolog a epilog funkce najdete v tématu [volání holé funkce](../cpp/naked-function-calls.md).  
  
 Informace o výchozích konvencí volání v kódu, který najdete v části cíle x64 platformy [přehled x64 konvence volání](../build/overview-of-x64-calling-conventions.md). Informace o volání konvence problémy v kódu, která je cílena ARM platformy najdete v tématu [běžné Visual C++ problémy s migrací ARM](../build/common-visual-cpp-arm-migration-issues.md).  
  
 Kompilátor Visual C/C++ jsou podporovány následující konvence volání.  
  
|– Klíčové slovo|Vymazání zásobníku|Předávání parametrů|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|volající|Nabízení parametry v zásobníku, v opačném pořadí (zprava doleva)|  
|[__clrcall](../cpp/clrcall.md)|není k dispozici|Načíst parametry do zásobníku výraz CLR v pořadí (zleva doprava).|  
|[__stdcall](../cpp/stdcall.md)|Volaný|Nabízení parametry v zásobníku, v opačném pořadí (zprava doleva)|  
|[__fastcall](../cpp/fastcall.md)|Volaný|Uložené v registrech, pak posunuto v zásobníku|  
|[__thiscall](../cpp/thiscall.md)|Volaný|Nabídnutých v zásobníku; **to** uložené v ECX ukazatele|  
|[__vectorcall](../cpp/vectorcall.md)|Volaný|Uložené v registrech, pak posunuto v zásobníku v obráceném pořadí (zprava doleva)|  
  
 Související informace najdete v tématu [zastaralé konvence volání](../cpp/obsolete-calling-conventions.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)