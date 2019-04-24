---
title: wcsrtombs
ms.date: 11/04/2016
apiname:
- wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: 46ef195ec4685c327c4b5951ec44e5c363214b59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155326"
---
# <a name="wcsrtombs"></a>wcsrtombs

Převeďte řetězec širokých znaků na jeho řetězcovou reprezentaci vícebajtového znaku. Bezpečnější verze této funkce je k dispozici. Zobrazit [wcsrtombs_s –](wcsrtombs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Výsledná převést umístění adresa vícebajtové znakové řetězce.

*wcstr*<br/>
Nepřímo odkazuje na umístění řetězec širokých znaků, který má být převeden.

*Počet*<br/>
Počet znaků, které má být převeden.

*mbstate*<br/>
Ukazatel **mbstate_t** převodu stavu objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů úspěšně převeden, bez zahrnutí null ukončující hodnotu null bajtů (pokud existuje), jinak -1, pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

**Wcsrtombs –** funkce převede řetězec širokých znaků, počínaje Zadaný převod stavu součástí *mbstate*, z hodnoty, na nepřímé v *wcstr*, do adresy *mbstr*. Převod bude pokračovat pro jednotlivé znaky, dokud: po nalezen null ukončující široké znaky, když je zjištěn bez odpovídající znak nebo při další znak by překročilo limit součástí *počet*. Pokud **wcsrtombs –** zaznamená prázdný znak širokého znaku (L '\0') před nebo po *počet* dojde, převede ho 8 bitů 0 a zastaví.

Proto vícebajtové znakové řetězce na *mbstr* je zakončený hodnotou null jenom v případě **wcsrtombs –** během převodu dojde prázdný znak širokého znaku. Pokud sekvence odkazované *wcstr* a *mbstr* překrývají, chování **wcsrtombs –** není definován. **wcsrtombs –** vliv podle kategorie LC_TYPE aktuálního národního prostředí.

**Wcsrtombs –** funkce se liší od [wcstombs – _wcstombs_l –](wcstombs-wcstombs-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány.  Například byste použili aplikaci **wcsrlen** spíše než **wcsnlen –**, pokud je následných volání **wcsrtombs –** používaly místo **wcstombs –**.

Pokud *mbstr* argument je **NULL**, **wcsrtombs –** vrací požadovaná velikost v bajtech cílový řetězec. Pokud *mbstate* má hodnotu null, vnitřní **mbstate_t** stav převodu se používá. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtové reprezentace znaku, vrátí se -1 a **errno** je nastavena na **EILSEQ**.

V jazyce C++ má tato funkce přetížení šablon, které vyvolá novější, zabezpečené protějšky této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcsrtombs –** funkce je bezpečné s více vlákny za předpokladu, žádné funkce v aktuálním vlákně volá **setlocale** při provádění této funkce a *mbstate* nemá hodnotu null.

## <a name="example"></a>Příklad

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
