---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328111"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Převeďte široký řetězec znaků na reprezentaci vícebajtového znakového řetězce. Verze [wcsrtombs](wcsrtombs.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Velikost v bajtů převedeného řetězce, včetně zakončení null.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný převedený vícebajtový znakový řetězec.

*sizeInBytes*<br/>
Velikost v bajtů vyrovnávací paměti *mbstr.*

*wcstr*<br/>
Odkazuje na široký řetězec znaků, který má být převeden.

*Počet*<br/>
Maximální počet bajtů, které mají být uloženy ve vyrovnávací paměti *MBSTR* nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na **objekt stavu mbstate_t** převodu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

|Chybový stav|Vrácená hodnota a **chybné číslo**|
|---------------------|------------------------------|
|*mbstr* je **NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* je **NULL**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá na to, aby obsahovala převedený řetězec (pokud není **_TRUNCATE** *počet;* viz poznámky níže)|**ERANGE**|

Pokud dojde k některé z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce vrátí kód chyby a nastaví **errno,** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **wcsrtombs_s** převede řetězec širokých znaků, na které je uvedeno *wcstr,* na vícebajtové znaky uložené ve vyrovnávací paměti, na které je odkazováno *nástrojem mbstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod bude pokračovat pro každý znak, dokud nebude splněna jedna z těchto podmínek:

- Je zjištěn znak null.

- Je zjištěn široký znak, který nelze převést.

- Počet bajtů uložených ve vyrovnávací paměti *mbstr* se rovná *počtu*.

Cílový řetězec je vždy ukončen nulou (i v případě chyby).

Pokud *count* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **pak wcsrtombs_s** převede tolik řetězce, jak se vejde do cílové vyrovnávací paměti, zatímco stále ponechává prostor pro null zakončení.

Pokud **wcsrtombs_s** úspěšně převede zdrojový řetězec, vloží velikost v bajtů převedeného řetězce, včetně zakončení null, do *&#42;pReturnValue* (za předpokladu, *že pReturnValue* není **NULL**). K tomu dochází i v *případě, že argument mbstr* je **null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud *mbstr* je **NULL**, *počet* je ignorována.

Pokud **wcsrtombs_s** narazí na široký znak nelze převést na vícebajtový znak, vloží -1 v * \*pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které se překrývají *wcstr* a *mbstr,* chování **wcsrtombs_s** není definováno. **wcsrtombs_s** je ovlivněna LC_TYPE kategorie aktuální národní prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odráží počet širokých znaků převést.

Funkce **wcsrtombs_s** se liší od [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) jeho restartability. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí. Například aplikace by použít **wcsrlen** spíše než **wcslen**, pokud následné volání **wcsrtombs_s** byly použity namísto **wcstombs_s**.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Wcsrtombs_s **wcsrtombs_s** funkce je bezpečné pro více vláken, pokud žádná funkce v aktuálním podprocesu volá **setlocale,** zatímco tato funkce je spuštěna a *mbstate* je null.

## <a name="example"></a>Příklad

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
