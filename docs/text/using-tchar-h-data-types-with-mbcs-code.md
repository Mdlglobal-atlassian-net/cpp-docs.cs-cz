---
title: Použití datových typů TCHAR.H s kódováním _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 78e5d89e1e87d081e762fab1298eb990b914324c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446590"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>Použití datových typů TCHAR.H s kódováním _MBCS

Když je definována konstanta manifestu `_MBCS`, je daná rutina obecného textu namapována na jeden z následujících typů rutin:

- Rutina SBCS, která vhodně zpracovává vícebajtové bajty, znaky a řetězce. V tomto případě se očekává, že řetězcové argumenty budou typu `char*`. Například `_tprintf` Maps `printf`; řetězcové argumenty pro `printf` jsou typu `char*`. Použijete-li datový typ `_TCHAR` obecný text pro typy řetězců, formální a skutečné typy parametrů `printf` shodují, protože `_TCHAR*` Maps `char*`.

- Rutina specifická pro znakovou sadu MBCS. V tomto případě se očekává, že řetězcové argumenty budou typu `unsigned char*`. Například `_tcsrev` mapuje na `_mbsrev`, která očekává a vrátí řetězec typu `unsigned char*`. Použijete-li datový typ `_TCHAR` obecný text pro vaše typy řetězců, může dojít ke konfliktu typu, protože `_TCHAR` mapování na typ `char`.

Níže jsou uvedena tři řešení pro prevenci tohoto konfliktu typu (a upozornění kompilátoru C nebo C++ chyby kompilátoru, které by mohly být výsledkem):

- Použijte výchozí chování. Tchar. h poskytuje prototypy rutiny obecného textu pro rutiny v běhových knihovnách, jak je uvedeno v následujícím příkladu.

    ```cpp
    char * _tcsrev(char *);
    ```

   Ve výchozím případu je prototyp pro `_tcsrev` namapován na `_mbsrev` prostřednictvím kódu v LIBC. lib. Tím se změní typy `_mbsrev` příchozích parametrů a odchozí návratová hodnota z `_TCHAR*` (tj. `char *`) na `unsigned char *`. Tato metoda zajišťuje, aby při použití `_TCHAR`bylo spárování typů, ale je relativně pomalé v důsledku režie volání funkce.

- Používejte vkládání funkcí, a to zahrnutím následujícího příkazu preprocesoru do kódu.

    ```cpp
    #define _USE_INLINING
    ```

   Tato metoda způsobí, že vložená funkce v Tchar. h namapuje rutinu obecného textu přímo na příslušnou rutinu znakové sady MBCS. Následující úryvek kódu z Tchar. h poskytuje příklad toho, jak je to provedeno.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   Pokud můžete použít vkládání, jedná se o nejlepší řešení, protože garantuje spárování typů a nemá žádné další časové náklady.

- Použijte přímé mapování zahrnutím následujícího příkazu preprocesoru do kódu.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   Tento přístup poskytuje rychlou alternativu, pokud nechcete použít výchozí chování nebo nelze použít vkládání. Způsobí, že rutina obecného textu bude mapována makrem přímo na verzi rutiny znakové sady MBCS, jak je uvedeno v následujícím příkladu z Tchar. h.

    ```cpp
    #define _tcschr _mbschr
    ```

   Když použijete tento přístup, musíte být opatrní, abyste zajistili použití vhodných datových typů pro řetězcové argumenty a návratové hodnoty řetězců. Můžete použít přetypování typů k zajištění správného odpovídajícího typu nebo můžete použít datový typ `_TXCHAR` obecný text. `_TXCHAR` mapuje na typ **char** v kódu SBCS, ale mapuje na typ **unsigned char** v kódu znakové sady MBCS. Další informace o makrech obecného textu naleznete v tématu [mapování obecných textových](../c-runtime-library/generic-text-mappings.md) informací v *knihovně run-time*.

## <a name="see-also"></a>Viz také

[Mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md)
