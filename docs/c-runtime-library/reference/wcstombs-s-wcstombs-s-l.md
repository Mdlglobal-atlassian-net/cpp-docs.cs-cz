---
title: wcstombs_s, _wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328051"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Převede posloupnost širokých znaků na odpovídající posloupnost vícebajtových znaků. Verze [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) s vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
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
Maximální počet bajtů pro uložení do vyrovnávací paměti *mbstr,* bez ukončujícího znaku null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

|Chybový stav|Vrácená hodnota a **chybné číslo**|
|---------------------|------------------------------|
|*mbstr* je **NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* je **NULL**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá na to, aby obsahovala převedený řetězec (pokud není **_TRUNCATE** *počet;* viz poznámky níže)|**ERANGE**|

Pokud dojde k některé z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce vrátí kód chyby a nastaví **errno,** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **wcstombs_s** převede řetězec širokých znaků, na které je uvedeno *wcstr,* na vícebajtové znaky uložené ve vyrovnávací paměti, na kterou poukazuje *mbstr*. Převod bude pokračovat pro každý znak, dokud nebude splněna jedna z těchto podmínek:

- Je zjištěn znak null.

- Je zjištěn široký znak, který nelze převést.

- Počet bajtů uložených ve vyrovnávací paměti *mbstr* se rovná *počtu*.

Cílový řetězec je vždy ukončen nulou (i v případě chyby).

Pokud *count* je speciální hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), pak **wcstombs_s** převede tolik řetězce, jak se vejde do cílové vyrovnávací paměti, zatímco stále ponechává prostor pro null zakončení. Pokud je řetězec zkrácen, vrácená hodnota je **STRUNCATE**a převod je považován za úspěšný.

Pokud **wcstombs_s** úspěšně převede zdrojový řetězec, vloží velikost v bajtů převedeného řetězce, včetně zakončení null, do *&#42;pReturnValue* (za předpokladu, *že pReturnValue* není **NULL**). K tomu dochází i v *případě, že argument mbstr* je **null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud *mbstr* je **NULL**, *počet* je ignorována.

Pokud **wcstombs_s** narazí na široký znak, nelze převést na vícebajtový znak, vloží 0 v *&#42;pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které se překrývají *wcstr* a *mbstr,* chování **wcstombs_s** není definováno.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odráží počet širokých znaků převést.

**wcstombs_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wcstombs_s_l** je totožný **s wcstombs** s tím rozdílem, že používá národní prostředí předané v místo. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování **wcstombs_s** funkce.

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
