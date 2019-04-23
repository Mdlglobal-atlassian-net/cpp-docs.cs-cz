---
title: wcstombs_s, _wcstombs_s_l
ms.date: 11/04/2016
apiname:
- _wcstombs_s_l
- wcstombs_s
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
ms.openlocfilehash: 6e17fd205d734e94b61d6b80d627a192d9448e29
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124990"
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s, _wcstombs_s_l

Převede sekvenci širokých znaků na odpovídající sekvence vícebajtových znaků. Verze [wcstombs – _wcstombs_l –](wcstombs-wcstombs-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Velikost v bajtech převedený řetězec, včetně ukončovacího znaku null.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný řetězec převedený vícebajtového znaku.

*sizeInBytes*<br/>
Velikost v bajtech *mbstr* vyrovnávací paměti.

*wcstr*<br/>
Odkazuje na řetězec širokých znaků, který má být převeden.

*Počet*<br/>
Maximální počet bajtů k ukládání *mbstr* vyrovnávací paměti, bez ukončujícího znaku null, nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby.

|Chybový stav|Vrátí hodnotu a **errno**|
|---------------------|------------------------------|
|*mbstr* je **NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* je **NULL**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (není-li *počet* je **_TRUNCATE**; viz poznámky níže)|**ERANGE**|

Pokud některá z těchto podmínek dojde k je vyvolána výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, funkce vrátí chybový kód a nastaví **errno** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

**Wcstombs_s –** funkce převede řetězec širokých znaků, na které odkazuje *wcstr* na vícebajtové znaky, které jsou uloženy ve vyrovnávací paměti, na které odkazuje *mbstr*. Převod bude pokračovat pro jednotlivé znaky, dokud nebude splněna jedna z těchto podmínek:

- Zjistil se široké znaky null

- Zjistil se široký znak, který nejde převést

- Počet bajtů uložených v *mbstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec je vždy zakončený (i v případě chyby).

Pokud *počet* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), pak **wcstombs_s –** převede největší část řetězce, jako se vejde do cílové vyrovnávací paměti a stále ponechají prostor s hodnotou Null ukončovací znak. Pokud je oříznutá. řetězec, návratovou hodnotou je **STRUNCATE**, a převod se považuje za úspěšné.

Pokud **wcstombs_s –** úspěšně převede zdrojový řetězec uloží velikost v bajtech převedený řetězec, včetně ukončovacího znaku null do  *&#42;pReturnValue* (k dispozici  *pReturnValue* není **NULL**). K tomu dojde i v případě, *mbstr* argument je **NULL** a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *mbstr* je **NULL**, *počet* se ignoruje.

Pokud **wcstombs_s –** nejde převést na vícebajtový znak, široký znak, zaznamená se vloží 0  *&#42;pReturnValue*, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví **errno**  k **EILSEQ**a vrátí **EILSEQ**.

Pokud sekvence odkazované *wcstr* a *mbstr* překrývají, chování **wcstombs_s –** není definován.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* nepřekrývají a že *počet* správně odráží počet širokých znaků pro převod.

**wcstombs_s –** používá aktuální národní prostředí pro všechna závislá chování; **_wcstombs_s_l –** je stejný jako **wcstombs –** s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ukazuje chování **wcstombs_s –** funkce.

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
