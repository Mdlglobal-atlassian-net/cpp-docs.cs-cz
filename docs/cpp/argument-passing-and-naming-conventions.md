---
title: Konvence předávání a pojmenování argumentů | Dokumentace Microsoftu
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
ms.openlocfilehash: 4e1a6a8e837a44a966f262f581db04f1589233c8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404038"
---
# <a name="argument-passing-and-naming-conventions"></a>Konvence předávání a pojmenování argumentů
**Specifické pro Microsoft**  
  
 Kompilátory jazyka Visual C++ umožňují určit konvence pro předávání argumentů a návratové hodnoty mezi funkcemi a volajícími. Ne všechny konvence jsou k dispozici na všech podporovaných platformách a některé konvence využívají implementace specifické pro platformu. Ve většině případů klíčová slova nebo přepínače kompilátoru určující nepodporovanou úmluvu na jednotlivých platformách jsou ignorovány a používá se výchozí konvence platformy.  
  
 Na x86 platformách, všechny argumenty jsou rozšířeny na 32 bitů, pokud jsou předány. Vrácené hodnoty jsou také rozšířeny na 32 bitů a vráceny v registru eax, kromě 8bytových struktur, které jsou následně vráceny v rejstříku páru edx: eax. Větší struktury jsou vráceny v registru eax jako ukazatele pro skryté struktury vrácení. Parametry jsou vloženy do zásobníku zprava doleva. Struktury, které nejsou pod, nebudou vráceny v registrech.  
  
 Kompilátor generuje kódu prologu a epilogu k uložení a obnovení registrů ESI, EDI, EBX a EBP zaregistruje, pokud jsou použity ve funkci.  
  
> [!NOTE]
>  Pokud struktura, unie nebo třída je vrácen z funkce hodnotou, všechny definice typu musí být stejné, jinak program může v době běhu selhat.  
  
 Informace o tom, jak definovat vlastní kód prologu a epilogu funkce naleznete v tématu [volání nahé funkce](../cpp/naked-function-calls.md).  
  
 Informace o výchozích konvencích volání v kódu, který najdete v článku cíle x64 platformy [přehled x64 konvence volání](../build/overview-of-x64-calling-conventions.md). Informace o potížích konvence volání v kódu, který cílí na platformy ARM naleznete v tématu [běžné Visual C++ ARM problémy s migrací](../build/common-visual-cpp-arm-migration-issues.md).  
  
 Kompilátor Visual C/C++ jsou podporovány následující konvence volání.  
  
|Klíčové slovo|Vymazání zásobníku|Předávání parametrů|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|Volající|Posune parametry zásobníku v opačném pořadí (zprava doleva)|  
|[__clrcall](../cpp/clrcall.md)|není k dispozici|Načítejte parametry do zásobníku výrazu CLR v pořadí (zleva doprava).|  
|[__stdcall](../cpp/stdcall.md)|/ Volaný|Posune parametry zásobníku v opačném pořadí (zprava doleva)|  
|[__fastcall](../cpp/fastcall.md)|/ Volaný|Uloží v registrech, poté vloženo do stohu|  
|[__thiscall](../cpp/thiscall.md)|/ Volaný|Posunuto v zásobníku; **to** ukazatel uložen v ECX|  
|[__vectorcall](../cpp/vectorcall.md)|/ Volaný|Uloží v registrech a odešle do zásobníku v opačném pořadí (zprava doleva)|  
  
 Související informace naleznete v tématu [zastaralé konvence volání](../cpp/obsolete-calling-conventions.md).  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Konvence volání](../cpp/calling-conventions.md)