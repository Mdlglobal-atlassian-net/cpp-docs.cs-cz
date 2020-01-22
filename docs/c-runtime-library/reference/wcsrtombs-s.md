---
title: wcsrtombs_s
ms.date: 11/04/2016
api_name:
- wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: 68f5b6f6b87fb3ad21899035dfc82d997d90cf38
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518306"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Převeďte řetězec s velkým znakem na jeho řetězcovou reprezentaci vícebajtových znaků. Verze [wcsrtombs](wcsrtombs.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Velikost převedeného řetězce v bajtech, včetně ukončovacího znaku null.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný převedený řetězec vícebajtových znaků.

*sizeInBytes*<br/>
Velikost *mbstr* vyrovnávací paměti v bajtech.

*wcstr*<br/>
Odkazuje na řetězec s velkým znakem, který má být převeden.

*count*<br/>
Maximální počet bajtů, které mají být uloženy v *mbstr* vyrovnávací paměti, nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na objekt stavu konverze **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání.

|Chybový stav|Návratová hodnota a **errno**|
|---------------------|------------------------------|
|*mbstr* má **hodnotu NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* má **hodnotu null** .|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá, aby obsahovala převedený řetězec (Pokud není *počet* **_TRUNCATE**; viz poznámky níže)|**ERANGE**|

Pokud nastane kterákoli z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce kód chyby a nastaví **errno** , jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **wcsrtombs_s** převádí řetězec velkých znaků, na které odkazoval *wcstr* na vícebajtové znaky uložené ve vyrovnávací paměti, na kterou ukazuje *mbstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod bude pro každý znak pokračovat, dokud nebude splněna jedna z těchto podmínek:

- Byl zjištěn velký znak null.

- Zjistil se velký znak, který se nedá převést.

- Počet bajtů uložených ve vyrovnávací paměti *mbstr* se rovná *počtu*.

Cílový řetězec je vždycky zakončený hodnotou null (i v případě chyby).

Pokud *Count* je speciální hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **wcsrtombs_s** se převede jako velká část řetězce, aby se vešla do cílové vyrovnávací paměti, zatímco pořád opouští místo pro ukončovací znak null.

Pokud **wcsrtombs_s** úspěšně převede zdrojový řetězec, vloží velikost v bajtech převedeného řetězce, včetně ukončovacího znaku null, do  *&#42;pReturnValue* (poskytnutý *pReturnValue* není **null**). K tomu dojde i v případě, že argument *mbstr* má **hodnotu null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud má *Mbstr* **hodnotu null**, *počet* se ignoruje.

Pokud **wcsrtombs_s** nalezne velký znak, nelze převést na vícebajtový znak, naplní-1 v *\*pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které ukazuje *wcstr* a *mbstr* , překrývají, chování **wcsrtombs_s** není definováno. **wcsrtombs_s** má vliv na kategorii LC_TYPE aktuálního národního prostředí.

> [!IMPORTANT]
> Zajistěte, aby se *wcstr* a *mbstr* nepřekrývaly a aby *počet* správně odpovídal počtu velkých znaků, které se mají převést.

Funkce **wcsrtombs_s** se liší od [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) podle jejich restartu. Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí. Například aplikace bude používat **wcsrlen** namísto **wcslen**, pokud bylo použito následné volání **wcsrtombs_s** místo **wcstombs_s**.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcsrtombs_s** je vláknově bezpečná, dokud žádná funkce v aktuálním vlákně nevolá funkci **setlocale** při provádění této funkce a *mbstate* má hodnotu null.

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
