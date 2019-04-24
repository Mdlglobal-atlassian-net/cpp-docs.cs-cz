---
title: wcrtomb_s
ms.date: 11/04/2016
apiname:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 7fe7fba861eecec562928cf381973f62a4db60fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155469"
---
# <a name="wcrtombs"></a>wcrtomb_s

Převeďte na její znázornění vícebajtový znak širokého znaku. Verze [wcrtomb –](wcrtomb.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Vrátí počet zapsaných bajtů nebo -1, pokud došlo k chybě.

*mbchar*<br/>
Výsledný vícebajtovou převede znak.

*sizeOfmbchar*<br/>
Velikost *mbchar* proměnné v bajtech.

*wchar*<br/>
Široký znak pro převod.

*mbstate*<br/>
Ukazatel **mbstate_t** objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu nebo **errno** hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Wcrtomb_s –** funkce převede široký znak, od Zadaný převod stavu součástí *mbstate*, oproti hodnotě obsažené v *wchar*, do Adresa reprezentována *mbchar*. *PReturnValue* hodnota bude počet bajtů převést, ale ne víc než **MB_CUR_MAX** bajtů nebo -1, pokud došlo k chybě.

Pokud *mbstate* má hodnotu null, vnitřní **mbstate_t** stav převodu se používá. Pokud součástí znak *wchar* nemá odpovídající vícebajtový znak, hodnotu *pReturnValue* bude mít hodnotu -1 a funkce vrátí hodnotu **errno** Hodnota **EILSEQ**.

**Wcrtomb_s –** funkce se liší od [wctomb_s – _wctomb_s_l –](wctomb-s-wctomb-s-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány. Například byste použili aplikaci **wcsrlen** spíše než **wcslen –**, pokud je následných volání **wcsrtombs_s –** používaly místo **wcstombs_s –**.

V jazyce C++ je použití této funkce zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcrtomb_s –** funkce je bezpečné s více vlákny za předpokladu, žádné funkce v aktuálním vlákně volá **setlocale** při provádění této funkce a *mbstate* má hodnotu null.

## <a name="example"></a>Příklad

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
