---
title: Použití datových typů TCHAR.H s kódováním _MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: b86cbc6d99cbc6969536934c1583ba5207a53629
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377883"
---
# <a name="using-tcharh-data-types-with-mbcs"></a>Použití datových typů TCHAR.H s kódováním _MBCS

**Microsoft Specific**

Jako označuje tabulky mapování rutin obecného textu (naleznete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md)), když konstanta manifestu **_MBCS** je definován, daný obecné textové rutiny mapuje na jednu z následujících typů z rutiny:

- Rutina SBCS, která zpracovává řetězce vícebajtové bajtů, znaky a odpovídajícím způsobem. V takovém případě se řetězcové argumenty očekává se typ **char&#42;**. Například **_tprintf** mapuje **printf**; řetězcové argumenty **printf** jsou typu **char&#42;**. Pokud používáte **_TCHAR** obecného textu datový typ pro váš řetězec typy, typy formální a skutečný parametr pro **printf** porovnat, protože **_TCHAR&#42;**  mapuje na **char&#42;**.

- Rutiny specifické znakové sady MBCS. V takovém případě se řetězcové argumenty očekává se typ __unsigned char&#42;__. Například **_tcsrev** mapuje **_mbsrev**, který očekává, že a vrátí řetězec typu __unsigned char&#42;__. Znovu Pokud použijete **_TCHAR** obecného textu datový typ pro vaše typy řetězců je potenciální konflikt typu protože **_TCHAR** mapuje na typ **char**.

Toto jsou tři řešení jak zabránit tomuto typu konfliktu (a upozornění kompilátoru jazyka C nebo chyby kompilátoru jazyka C++, které by vedla k):

- Použije výchozí chování. TCHAR. H zajišťující prototypy obecné textové rutiny knihoven runtime, jako v následujícím příkladu.

   ```C
   char *_tcsrev(char *);
   ```

   Ve výchozím nastavení, prototyp **_tcsrev** mapuje **_mbsrev** prostřednictvím převodní rutina v LIBC. LIB. Typy se tím změní **_mbsrev** příchozí parametry a odchozí vrátit hodnotu z **_TCHAR &#42;**  (například **char &#42;** ) k **unsigned char &#42;**. Tato metoda zajišťuje typ odpovídající při použití **_TCHAR**, ale je poměrně pomalý kvůli režii volání funkce.

- Pomocí funkce vkládání začleňte následující příkaz preprocesoru ve vašem kódu.

   ```C
   #define _USE_INLINING
   ```

   Tato metoda způsobí, že vložené funkce převodní rutinou, součástí TCHAR. H mapování obecného textu rutina přímo do příslušné rutiny znakové sady MBCS. Následující úryvek kódu z TCHAR. H znázorňuje, jak to lze provést.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   Pokud vám vkládání, toto je doporučené řešení, zaručuje zadejte odpovídající a obsahuje náklady. žádné další čas.

- Použijte "přímé mapování" začleňte následující příkaz preprocesoru ve vašem kódu.

   ```C
   #define _MB_MAP_DIRECT
   ```

   Tento přístup poskytuje rychlou alternativou, pokud nechcete použít výchozí chování nebo nemůže používat vložené. Způsobí, že rutina obecného textu namapovat tak makro přímo na verzi znakové sady MBCS rutiny, jako v následujícím příkladu od TCHAR. H.

   ```C
   #define _tcschr _mbschr
   ```

Při volbě této možnosti musí být opatrní a zajistit, že příslušné datové typy se používají pro argumenty řetězce a vrácené hodnoty řetězce. Přetypování typu můžete použít k zajištění shody správný typ, nebo můžete použít **_TXCHAR** datový typ obecného textu. **_TXCHAR** mapuje na typ **char** v kódu SBCS ale mapování na typ **unsigned char** v kódu znakové sady MBCS. Další informace o makra obecného textu, naleznete v tématu [mapování obecného textu](../c-runtime-library/generic-text-mappings.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
