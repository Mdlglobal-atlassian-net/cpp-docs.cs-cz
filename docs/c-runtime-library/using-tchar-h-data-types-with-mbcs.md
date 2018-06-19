---
title: Pomocí Tchar –. Datové typy H s kódováním _MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 066459593be4970fde141333a6f22f0846f8bbc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412648"
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Použití datových typů TCHAR.H s kódováním _MBCS

**Konkrétní Microsoft**

Jako tabulka mapování obecného textu rutiny udává (najdete v části [mapování obecného textu](../c-runtime-library/generic-text-mappings.md)), když manifestu konstanta **_MBCS** je definován, daná rutina obecného textu se mapuje na jednu z následujících typů z rutiny:

- Rutina SBCS, která zpracovává vícebajtové bajtů, znaky a řetězce správně. V takovém případě jsou očekávány řetězcové argumenty být typu **char&#42;**. Například **_tprintf –** mapuje **printf**; argumenty řetězce, které mají **printf** typu **char&#42;**. Pokud použijete **_TCHAR** obecného textu datový typ řetězec vašeho typy, typy formální a aktuální parametrů pro **printf** souhlasit, protože **_TCHAR&#42;**  mapuje **char&#42;**.

- Rutiny specifické pro MBCS. V takovém případě jsou očekávány řetězcové argumenty být typu __nepodepsané char&#42;__. Například **_tcsrev** mapuje **_mbsrev**, která očekává a vrátí řetězec typu __nepodepsané char&#42;__. Znovu Pokud použijete **_TCHAR** obecného textu datový typ pro vaše typy řetězců nastal konflikt typu potenciální protože **_TCHAR** mapuje na typ **char**.

 Toto jsou tři řešení pro prevenci tento konflikt typu (a upozornění kompilátoru jazyka C nebo C++ chyby kompilátoru, které by):

- Použije výchozí chování. TCHAR –. H poskytuje prototypy obecného textu pro rutiny v běhové knihovny, jako v následujícím příkladu.

   ```C
   char *_tcsrev(char *);
   ```

   V případě výchozí prototypu pro **_tcsrev** mapuje **_mbsrev** prostřednictvím převodu v LIBC. LIB. Tato operace změní typy **_mbsrev –** příchozí parametry a odchozí návratová hodnota z **_TCHAR – &#42;**  (například **char &#42;** ) k **nepodepsané char &#42;**. Tato metoda zajišťuje typ odpovídající při použití **_TCHAR**, ale je relativně pomalá kvůli režii volání funkce.

- Pomocí funkce vložené začleněním následující preprocesoru ve vašem kódu.

   ```C
   #define _USE_INLINING
   ```

   Tato metoda způsobí, že převodu vložené funkce, součástí Tchar –. H k mapování obecného textu rutiny přímo do příslušné rutiny MBCS. Následující výpis kódu z Tchar –. H poskytuje příklad, jak to provést.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Pokud můžete použít vložené, toto je nejlepší řešení, protože zaručuje, zadejte odpovídající a obsahuje náklady. žádné další čas.

- Použijte "přímé mapování" začleněním následující preprocesoru ve vašem kódu.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Tento přístup poskytuje rychlou alternativu, pokud nechcete použít výchozí chování nebo nemůže používat vložené. Způsobí, že rutina obecného textu nejde mapovat pomocí makra přímo na verzi MBCS rutiny, jako v následujícím příkladu z Tchar –. H.

   ```C
   #define _tcschr _mbschr
   ```

Pokud tuto metodu, musí být opatrní, abyste zajistili, že příslušné datové typy se používají pro argumenty řetězce a návratové hodnoty řetězce. Přetypování typu můžete použít k zajištění správné shody typů nebo můžete použít **_TXCHAR** datový typ obecného textu. **_TXCHAR –** mapuje na typ **char** v kódu SBCS ale mapuje na typ **nepodepsané char** v MBCS kódu. Další informace o obecného textu makra najdete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md).

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
