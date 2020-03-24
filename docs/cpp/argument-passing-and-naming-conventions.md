---
title: Konvence předávání a pojmenování argumentů
ms.date: 12/17/2018
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
ms.openlocfilehash: e621db339102f1f40030bc7826d383d306a39be8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190765"
---
# <a name="argument-passing-and-naming-conventions"></a>Konvence předávání a pojmenování argumentů

**Specifické pro společnost Microsoft**

Kompilátory C++ Microsoftu umožňují určit konvence předávání argumentů a návratové hodnoty mezi funkcemi a volajícími. Ne všechny konvence jsou k dispozici na všech podporovaných platformách a některé konvence používají implementace specifické pro konkrétní platformu. Ve většině případů se klíčová slova nebo přepínače kompilátoru, které určují nepodporovanou konvenci na konkrétní platformě, ignorují a použije se výchozí konvence platformy.

Na platformě x86 platformách jsou všechny argumenty rozšířeny na 32 bitů, když jsou předány. Návratové hodnoty jsou také rozšířeny na 32 bitů a vráceny v registru EAX vrátí, s výjimkou 8bitových struktur, které jsou vráceny ve dvojici registru EDX: EAX vrátí. Větší struktury se vrátí v registru EAX vrátí jako ukazatelé na skryté návratové struktury. Parametry jsou vloženy do zásobníku zprava doleva. Struktury, které nejsou lusky, nebudou vráceny v registrech.

Kompilátor generuje kód prologu a epilogu pro uložení a obnovení registrů ESI, EDI, EBX a EBP, pokud jsou použity ve funkci.

> [!NOTE]
> Při vrácení struktury, sjednocení nebo třídy z funkce podle hodnoty musí být všechny definice typu stejné, jinak program může za běhu selhat.

Informace o tom, jak definovat vlastní prolog a Kód epilogu funkce, najdete v tématu [volání holé funkce](../cpp/naked-function-calls.md).

Informace o výchozích konvencích volání v kódu, které cílí na platformy x64, naleznete v tématu [konvence volání x64](../build/x64-calling-convention.md). Informace o problémech s konvencí volání v kódu, který cílí na platformy ARM, najdete v tématu [běžné problémy s migrací v nástroji C++ Visual ARM](../build/common-visual-cpp-arm-migration-issues.md).

Následující konvence volání jsou podporovány jazykem Visual C/C++ kompilátor.

|Klíčové slovo|Vyčištění zásobníku|Předávání parametrů|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Volající|Posune parametry v zásobníku v opačném pořadí (zprava doleva).|
|[__clrcall](../cpp/clrcall.md)|neuvedeno|Načíst parametry do zásobníku výrazu CLR v pořadí (zleva doprava).|
|[__stdcall](../cpp/stdcall.md)|Volaný|Posune parametry v zásobníku v opačném pořadí (zprava doleva).|
|[__fastcall](../cpp/fastcall.md)|Volaný|Uloženo v registrech a pak vloženo do zásobníku|
|[__thiscall](../cpp/thiscall.md)|Volaný|Vloženo do zásobníku; **Tento** ukazatel uložený v ecx|
|[__vectorcall](../cpp/vectorcall.md)|Volaný|Uloženo v registrech a pak vloženo do zásobníku v opačném pořadí (zprava doleva)|

Související informace naleznete v tématu [zastaralé konvence volání](../cpp/obsolete-calling-conventions.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)
