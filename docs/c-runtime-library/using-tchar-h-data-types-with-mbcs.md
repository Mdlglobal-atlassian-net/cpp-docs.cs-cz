---
title: "Pomocí Tchar –. Datové typy H s kódováním _MBCS | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c015c8ff7481f0d5ba25eba023b21f4877deaa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Použití datových typů TCHAR.H s kódováním _MBCS
**Konkrétní Microsoft**  
  
 Jako tabulka mapování obecného textu rutiny udává (najdete v části [mapování obecného textu](../c-runtime-library/generic-text-mappings.md)), když manifestu konstanta `_MBCS` je definován, daná rutina obecného textu se mapuje na jednu z následujících druhů rutin:  
  
-   Rutina SBCS, která zpracovává vícebajtové bajtů, znaky a řetězce správně. V takovém případě jsou očekávány řetězcové argumenty být typu `char*`. Například `_tprintf` mapuje `printf`; argumenty řetězce, které mají `printf` typu `char*`. Pokud použijete `_TCHAR` obecného textu datový typ řetězec vašeho typy, typy formální a aktuální parametrů pro `printf` souhlasit, protože `_TCHAR*` mapuje `char*`.  
  
-   Rutiny specifické pro MBCS. V takovém případě jsou očekávány řetězcové argumenty být typu `unsigned char*`. Například `_tcsrev` mapuje `_mbsrev`, která očekává a vrátí řetězec typu `unsigned char*`. Znovu Pokud použijete `_TCHAR` obecného textu datový typ pro vaše typy řetězců nastal konflikt typu potenciální protože `_TCHAR` mapuje na typ `char`.  
  
 Toto jsou tři řešení pro prevenci tento konflikt typu (a upozornění kompilátoru jazyka C nebo C++ chyby kompilátoru, které by):  
  
-   Použije výchozí chování. TCHAR –. H poskytuje prototypy obecného textu pro rutiny v běhové knihovny, jako v následujícím příkladu.  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     V případě výchozí prototypu pro `_tcsrev` mapuje `_mbsrev` prostřednictvím převodu v LIBC. LIB. Tato operace změní typy `_mbsrev` příchozí parametry a odchozí návratová hodnota z `_TCHAR *` (například `char *`) k `unsigned char *`. Tato metoda zajišťuje typ odpovídající při použití `_TCHAR`, ale je relativně pomalá kvůli režii volání funkce.  
  
-   Pomocí funkce vložené začleněním následující preprocesoru ve vašem kódu.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     Tato metoda způsobí, že převodu vložené funkce, součástí Tchar –. H k mapování obecného textu rutiny přímo do příslušné rutiny MBCS. Následující výpis kódu z Tchar –. H poskytuje příklad, jak to provést.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     Pokud můžete použít vložené, toto je nejlepší řešení, protože zaručuje, zadejte odpovídající a obsahuje náklady. žádné další čas.  
  
-   Použijte "přímé mapování" začleněním následující preprocesoru ve vašem kódu.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Tento přístup poskytuje rychlou alternativu, pokud nechcete použít výchozí chování nebo nemůže používat vložené. Způsobí, že rutina obecného textu nejde mapovat pomocí makra přímo na verzi MBCS rutiny, jako v následujícím příkladu z Tchar –. H.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 Pokud tuto metodu, musí být opatrní, abyste zajistili, že příslušné datové typy se používají pro argumenty řetězce a návratové hodnoty řetězce. Přetypování typu můžete použít k zajištění správné shody typů nebo můžete použít `_TXCHAR` datový typ obecného textu. `_TXCHAR`mapuje na typ `char` v kódu SBCS ale mapuje na typ `unsigned char` v MBCS kódu. Další informace o obecného textu makra najdete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Internacionalizace](../c-runtime-library/internationalization.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)