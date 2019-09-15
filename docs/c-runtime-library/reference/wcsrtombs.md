---
title: wcsrtombs
ms.date: 11/04/2016
api_name:
- wcsrtombs
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: e6640a027b03b7aa0dceaf8e61af6cb43a44d6e0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945051"
---
# <a name="wcsrtombs"></a>wcsrtombs

Převeďte řetězec s velkým znakem na jeho řetězcovou reprezentaci vícebajtových znaků. K dispozici je bezpečnější verze této funkce; viz [wcsrtombs_s](wcsrtombs-s.md).

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
Výsledný převedený adresní pozici vícebajtového řetězce znaků.

*wcstr*<br/>
Nepřímo odkazuje na umístění řetězce s velkým znakem, který má být převeden.

*výpočtu*<br/>
Počet znaků, který má být převeden.

*mbstate*<br/>
Ukazatel na objekt stavu převodu **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Vrátí počet převedených bajtů, včetně nulového ukončujícího bajtu null (pokud existuje), v opačném případě a-1, pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcsrtombs** převádí řetězec velkých znaků, počínaje v zadaném stavu konverze obsaženém v *mbstate*, z hodnot nepřímých ukázání na v *wcstr*, do adresy *mbstr*. Převod bude pro každý znak pokračovat až po výskytu prázdného koncového znaku, pokud je nalezen neodpovídající znak nebo pokud by další znak překročil limit obsažený v *počtu*. Pokud **wcsrtombs** nalezne znak null znaků (L ' \ 0 ') před *nebo po* výskytu, převede ho na 8 bitů 0 a zastaví.

Proto je řetězec vícebajtového znaku na *mbstr* zakončený hodnotou null pouze v případě, že **wcsrtombs** během konverze narazí na znak null s velkým znakem. Pokud se sekvence, na které ukazuje *wcstr* a *mbstr* , překrývají, chování **wcsrtombs** není definováno. **wcsrtombs** je ovlivněna kategorií LC_TYPE aktuálního národního prostředí.

Funkce **wcsrtombs** se od jejího spuštění liší od [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) . Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí.  Například aplikace bude používat **wcsrlen** namísto **wcsnlen**, pokud bylo použito následné volání **wcsrtombs** namísto **wcstombs**.

Pokud má argument *Mbstr* **hodnotu null**, **wcsrtombs** vrátí požadovanou velikost v bajtech cílového řetězce. Pokud má *mbstate* hodnotu null, použije se vnitřní stav konverze **mbstate_t** . Pokud znak sekvence *WCHAR* neobsahuje odpovídající vícebajtovou reprezentaci znaků, je vrácena znak-1 a **errno** je nastaven na hodnotu **EILSEQ**.

V C++systému má tato funkce přetížení šablony, které vyvolá novější a zabezpečený protějšek této funkce. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcsrtombs** je vláknově bezpečná, dokud žádná funkce v aktuálním vlákně nevolá **setlocale** při provádění této funkce a *mbstate* není null.

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
