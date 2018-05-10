---
title: Pomocí Tchar –. Datové typy H s kódováním _MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
- TCHAR
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e80ecd123e3fc47705563156e33f46ecd99a0321
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="using-tcharh-data-types-with-mbcs-code"></a>Použití datových typů TCHAR.H s kódováním _MBCS
Když manifestu konstanta **_MBCS** je definován, daná rutina obecného textu se mapuje na jednu z následujících druhů rutin:  
  
-   Rutina SBCS, která zpracovává vícebajtové bajtů, znaky a řetězce správně. V takovém případě jsou očekávány řetězcové argumenty být typu **char\***. Například `_tprintf` mapuje `printf`; argumenty řetězce, které mají `printf` typu **char\***. Pokud používáte **_TCHAR** obecného textu datový typ řetězec vašeho typy, typy formální a aktuální parametrů pro `printf` souhlasit, protože **_TCHAR** \* mapuje **char \***.  
  
-   Rutiny specifické pro MBCS. V takovém případě jsou očekávány řetězcové argumenty být typu `unsigned` **char\***. Například `_tcsrev` mapuje `_mbsrev`, která očekává a vrátí řetězec typu `unsigned` **char\***. Pokud použijete **_TCHAR** obecného textu datový typ pro vaše typy řetězců nastal konflikt typu potenciální protože **_TCHAR** mapuje na typ `char`.  
  
 Toto jsou tři řešení pro prevenci tento konflikt typu (a upozornění kompilátoru jazyka C nebo C++ chyby kompilátoru, které by):  
  
-   Použije výchozí chování. Tchar.h poskytuje prototypy obecného textu pro rutiny v běhové knihovny, jako v následujícím příkladu.  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     V případě výchozí prototypu pro `_tcsrev` mapuje `_mbsrev` prostřednictvím převodu v Libc.lib. Tato operace změní typy `_mbsrev` příchozí parametry a odchozí návratová hodnota z **_TCHAR \***  (to znamená, `char` **\***) k `unsigned` `char` **\***. Tato metoda zajišťuje typ odpovídající při použití **_TCHAR**, ale je relativně pomalá kvůli režii volání funkce.  
  
-   Pomocí funkce vložené začleněním následující preprocesoru ve vašem kódu.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Tato metoda způsobí, že převodu vložené funkce, zadaný v souboru Tchar.h k mapování obecného textu rutiny přímo do příslušné rutiny MBCS. Následující výpis kódu z Tchar.h poskytuje příklad, jak to provést.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     Pokud můžete použít vložené, toto je nejlepší řešení, protože zaručuje, zadejte odpovídající a obsahuje náklady. žádné další čas.  
  
-   Použijte přímé mapování začleněním následující preprocesoru ve vašem kódu.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Tento přístup poskytuje rychlou alternativu, pokud nechcete použít výchozí chování nebo nemůže používat vložené. Způsobí, že rutina obecného textu nejde mapovat pomocí makra přímo na verzi MBCS rutiny, jako v následujícím příkladu z Tchar.h.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     Pokud tuto metodu, musí být opatrní, abyste zajistili použití příslušné datové typy pro argumenty řetězce a návratové hodnoty řetězce. Přetypování typu můžete použít k zajištění správné shody typů nebo můžete použít **_TXCHAR** datový typ obecného textu. **_TXCHAR –** mapuje na typ `char` v kódu SBCS ale mapuje na typ `unsigned` `char` v MBCS kódu. Další informace o obecného textu makra najdete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="see-also"></a>Viz také  
 [Mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md)