---
title: wcrtomb
ms.date: 11/04/2016
apiname:
- wcrtomb
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: a5fad3f41c7ed459a1af3fae7c6a5a85c867d5ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659248"
---
# <a name="wcrtomb"></a>wcrtomb

Převeďte na její znázornění vícebajtový znak širokého znaku. Bezpečnější verze této funkce je k dispozici. Zobrazit [wcrtomb_s –](wcrtomb-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Výsledný vícebajtovou převede znak.

*wchar*<br/>
Široký znak pro převod.

*mbstate*<br/>
Ukazatel **mbstate_t** objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů potřebných k zastoupení převedený vícebajtový znak, jinak -1 Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Wcrtomb –** funkce převede široký znak, od Zadaný převod stavu součástí *mbstate*, oproti hodnotě obsažené v *wchar*, do Adresa reprezentována *mbchar*. Vrácená hodnota je počet bajtů potřebných k zastoupení odpovídající vícebajtový znak, ale nebudou nalezeny více než **MB_CUR_MAX** bajtů.

Pokud *mbstate* má hodnotu null, vnitřní **mbstate_t** objekt, který obsahuje stav převodu *mbchar* se používá. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtové reprezentace znaku, vrátí se -1 a **errno** je nastavena na **EILSEQ**.

**Wcrtomb –** funkce se liší od [wctomb – _wctomb_l –](wctomb-wctomb-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány. Například byste použili aplikaci **wcsrlen** spíše než **wcsnlen –**, pokud je následných volání **wcsrtombs –** používaly místo **wcstombs –**.

V jazyce C++ má tato funkce přetížení šablon, které vyvolá novější, zabezpečené protějšky této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcrtomb –** funkce je bezpečné s více vlákny za předpokladu, žádné funkce v aktuálním vlákně volá **setlocale** při provádění této funkce a při *mbstate* má hodnotu null.

## <a name="example"></a>Příklad

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
