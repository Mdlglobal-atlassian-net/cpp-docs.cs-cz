---
title: Použití příkazu VERIFY místo ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: bfc0847677ae232fef67ab6200c626472f042bdb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438621"
---
# <a name="using-verify-instead-of-assert"></a>Použití příkazu VERIFY místo ASSERT

Předpokládejme, že při spuštění ladicí verze aplikace MFC nejsou k dispozici žádné problémy. Verze pro vydání stejné aplikace ale selže, vrátí nesprávné výsledky nebo se projeví v jiném neobvyklém chování.

K tomuto problému může dojít při umísťování důležitého kódu do příkazu KONTROLNÍho výrazu pro ověření, že funguje správně. Vzhledem k tomu, že příkazy ASSERT jsou zakomentovány v sestavení pro vydání programu knihovny MFC, kód neběží v buildu pro vydání.

Pokud používáte ASSERT k potvrzení, že volání funkce bylo úspěšné, zvažte místo toho použití [ověření](../mfc/reference/diagnostic-services.md#verify) . Makro VERIFY vyhodnotí své vlastní argumenty v sestaveních ladění i vydaných verzí aplikace.

Další upřednostňovanou technikou je přiřadit návratovou hodnotu funkce dočasnou proměnnou a potom otestovat proměnnou v příkazu KONTROLNÍho výrazu.

Projděte si následující fragment kódu:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Tento kód funguje dokonale v ladicí verzi aplikace MFC. Pokud se volání `calloc( )` nezdařilo, zobrazí se diagnostická zpráva, která obsahuje soubor a číslo řádku. V maloobchodním sestavení aplikace MFC však:

- volání `calloc( )` nikdy neproběhne, je ponecháno `buf` neinicializované nebo

- `strcpy_s( )`zkopíruje "`Hello, World`" do náhodné paměti, může způsobit chybu aplikace nebo způsobit, že systém přestane reagovat.

- `free()`pokusí se uvolnit paměť, která nebyla nikdy přidělena.

Chcete-li použít vyhodnocení správně, je třeba změnit vzorek kódu na následující:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Nebo můžete místo toho použít možnost ověřit:

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Viz také

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
