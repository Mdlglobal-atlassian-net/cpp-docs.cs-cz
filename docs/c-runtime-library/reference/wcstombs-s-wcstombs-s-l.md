---
title: wcstombs_s, _wcstombs_s_l
ms.date: 11/04/2016
api_name:
- _wcstombs_s_l
- wcstombs_s
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
ms.openlocfilehash: 135bcb90e6a82591bf05e56b60575719f4c7d45c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945028"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Převede sekvenci velkých znaků na odpovídající sekvenci vícebajtových znaků. Verze [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Velikost převedeného řetězce v bajtech, včetně ukončovacího znaku null.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný převedený řetězec vícebajtových znaků.

*sizeInBytes*<br/>
Velikost *mbstr* vyrovnávací paměti v bajtech.

*wcstr*<br/>
Odkazuje na řetězec s velkým znakem, který má být převeden.

*výpočtu*<br/>
Maximální počet bajtů, které se mají Uložit do vyrovnávací paměti *mbstr* , včetně ukončujícího znaku null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání.

|Chybový stav|Návratová hodnota a **errno**|
|---------------------|------------------------------|
|*mbstr* má **hodnotu NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* má **hodnotu null** .|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá, aby obsahovala převedený řetězec (Pokud není *počet* **_TRUNCATE**; viz poznámky níže)|**ERANGE**|

Pokud nastane kterákoli z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce kód chyby a nastaví **errno** , jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **wcstombs_s** převede řetězec velkých znaků, na které ukazuje *wcstr* na vícebajtové znaky uložené ve vyrovnávací paměti, na které ukazuje *mbstr*. Převod bude pro každý znak pokračovat, dokud nebude splněna jedna z těchto podmínek:

- Byl zjištěn velký znak null.

- Zjistil se velký znak, který se nedá převést.

- Počet bajtů uložených ve vyrovnávací paměti *mbstr* se rovná *počtu*.

Cílový řetězec je vždycky zakončený hodnotou null (i v případě chyby).

Pokud *Count* je speciální hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **wcstombs_s** se převede jako velká část řetězce, aby se vešla do cílové vyrovnávací paměti, zatímco pořád opouští místo ukončovacího znaku null. Pokud je řetězec zkrácen, návratová hodnota je **STRUNCATE**a převod je považován za úspěšný.

Pokud **wcstombs_s** úspěšně převede zdrojový řetězec, vloží velikost v bajtech převedeného řetězce, včetně ukončovacího znaku null, do  *&#42;pReturnValue* (poskytnutý *pReturnValue* není **null**). K tomu dojde i v případě, že argument *mbstr* má **hodnotu null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud má *Mbstr* **hodnotu null**, *počet* se ignoruje.

Pokud **wcstombs_s** narazí na velký znak, nemůže převést na vícebajtový znak, bude mít 0 v  *&#42;pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které ukazuje *wcstr* a *mbstr* , překrývají, chování **wcstombs_s** není definováno.

> [!IMPORTANT]
> Zajistěte, aby se *wcstr* a *mbstr* nepřekrývaly a aby *počet* správně odpovídal počtu velkých znaků, které se mají převést.

**wcstombs_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wcstombs_s_l** je shodná s **wcstombs** s tím rozdílem, že místo toho používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování funkce **wcstombs_s** .

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
