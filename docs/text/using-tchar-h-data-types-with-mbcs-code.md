---
title: Použití datových typů TCHAR.H s kódováním _MBCS
ms.date: 11/04/2016
f1_keywords:
- TCHAR
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 0e26aefd8b9099a2ca5e76ce9e2b7d1def2f9854
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813822"
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Použití datových typů TCHAR.H s kódováním _MBCS

Když konstanta manifestu `_MBCS` je definován, dané rutiny obecného textu mapuje na jednu z následujících druhů rutin:

- Rutina SBCS, která zpracovává řetězce vícebajtové bajtů, znaky a odpovídajícím způsobem. V takovém případě se řetězcové argumenty očekává se typ `char*`. Například `_tprintf` mapuje `printf`; řetězcové argumenty `printf` jsou typu `char*`. Pokud používáte `_TCHAR` obecného textu datový typ pro váš řetězec typy, typy formální a skutečný parametr pro `printf` porovnat, protože `_TCHAR*` mapuje `char*`.

- Rutiny specifické znakové sady MBCS. V takovém případě se řetězcové argumenty očekává se typ `unsigned char*`. Například `_tcsrev` mapuje `_mbsrev`, který očekává, že a vrátí řetězec typu `unsigned char*`. Pokud používáte `_TCHAR` obecného textu datový typ pro vaše typy řetězců je potenciální konflikt typu protože `_TCHAR` mapuje na typ `char`.

Toto jsou tři řešení jak zabránit tomuto typu konfliktu (a upozornění kompilátoru jazyka C nebo chyby kompilátoru jazyka C++, které by vedla k):

- Použije výchozí chování. Tchar.h zajišťující prototypy obecné textové rutiny knihoven runtime, jako v následujícím příkladu.

    ```cpp
    char * _tcsrev(char *);
    ```

   Ve výchozím nastavení, prototyp `_tcsrev` mapuje `_mbsrev` prostřednictvím převodní rutina v Libc.lib. Typy se tím změní `_mbsrev` příchozí parametry a odchozí vrátit hodnotu z `_TCHAR*` (to znamená `char *`) k `unsigned char *`. Tato metoda zajišťuje shodu při použití typů `_TCHAR`, ale je poměrně pomalý kvůli režii volání funkce.

- Pomocí funkce vkládání začleňte následující příkaz preprocesoru ve vašem kódu.

    ```cpp
    #define _USE_INLINING
    ```

   Tato metoda způsobí, že vložené funkce převodní rutinou, uvedené v souboru tchar.h se k mapování obecného textu rutina přímo do příslušné rutiny znakové sady MBCS. Následující úryvek kódu ze souboru tchar.h znázorňuje, jak to lze provést.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Pokud vám vkládání, toto je doporučené řešení, zaručuje zadejte odpovídající a obsahuje náklady. žádné další čas.

- Použijte přímé mapování začleňte následující příkaz preprocesoru ve vašem kódu.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Tento přístup poskytuje rychlou alternativou, pokud nechcete použít výchozí chování nebo nemůže používat vložené. Způsobí, že obecné textové rutiny namapovat tak makro přímo na verzi znakové sady MBCS rutiny, jako v následujícím příkladu v souboru tchar.h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Při volbě této možnosti musí být opatrní a zajistit používání odpovídající datových typů pro argumenty řetězce a vrácené hodnoty řetězce. Přetypování typu můžete použít k zajištění shody správný typ, nebo můžete použít `_TXCHAR` datový typ obecného textu. `_TXCHAR` mapování na typ **char** v kódu SBCS ale mapování na typ **unsigned char** v kódu znakové sady MBCS. Další informace o makra obecného textu, naleznete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md) v *Run-Time Library Reference*.

## <a name="see-also"></a>Viz také:

[Mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md)
