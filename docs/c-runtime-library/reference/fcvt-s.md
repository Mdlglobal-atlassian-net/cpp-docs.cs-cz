---
title: _fcvt_s
ms.date: 04/05/2018
apiname:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: 51ff3c675f1f53aee9beab629b17193164a2e7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536845"
---
# <a name="fcvts"></a>_fcvt_s

Převede číslo s plovoucí desetinnou čárkou na řetězec. Toto je verze [_fcvt –](fcvt.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _fcvt_s(
   char* buffer,
   size_t sizeInBytes,
   double value,
   int count,
   int *dec,
   int *sign
);
template <size_t size>
errno_t _fcvt_s(
   char (&buffer)[size],
   double value,
   int count,
   int *dec,
   int *sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Poskytnutá vyrovnávací paměť, která bude obsahovat výsledku převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*value*<br/>
Číslo, které má být převeden.

*Počet*<br/>
Počet číslic za desetinnou čárkou.

*DEC*<br/>
Ukazatel pozice uložené desetinné čárky.

*sign*<br/>
Ukazatel na ukazatel uložené přihlašování.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Seznam těchto chyb, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru, jak je uvedeno v následující tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*sizeInBytes*|value|count|dec|znak|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**HODNOTU NULL**|Všechny|Všechny|Všechny|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|<=0|Všechny|Všechny|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Všechny|Všechny|Všechny|Všechny|**HODNOTU NULL**|Všechny|**EINVAL**|Nedojde ke změně.|
|Všechny|Všechny|Všechny|Všechny|Všechny|**HODNOTU NULL**|**EINVAL**|Nedojde ke změně.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_fcvt_s –** může vygenerovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Fcvt_s –** funkce převede číslo s plovoucí desetinnou čárkou na řetězec znaků zakončené znakem null. *Hodnotu* parametru je číslo s plovoucí desetinnou čárkou má být převeden. **_fcvt_s –** ukládá na číslice *hodnota* jako řetězec a připojí znak null ('\0'). *Počet* parametr určuje počet číslic, které mají být uloženy za desetinnou čárkou. Jsou nadbytečné číslic zaokrouhlena *počet* umístí. Pokud jsou kratší než *počet* číslicemi přesnosti, řetězec je doplněny nulami.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* můžete získat *dec* a *přihlašování* po volání. *Dec* parametr odkazuje na celočíselnou hodnotu; poskytuje tuto hodnotu celého čísla pozici od desetinné čárky s ohledem na začátku řetězce. Nula nebo záporné celé číslo označuje, zda desetinné čárky je nalevo od první číslice. Parametr *přihlašování* odkazuje na celé číslo označující znaménko *hodnota*. Celé číslo je nastavena na 0, pokud *hodnotu* kladné a nastaven na nenulovou hodnotu, počet Pokud *hodnotu* je záporný.

Vyrovnávací paměť o délce **_CVTBUFSIZE** je dostatečná pro všechny plovoucí desetinnou čárkou.

Rozdíl mezi **_ecvt_s –** a **_fcvt_s –** probíhá vyhodnocení *počet* parametru. **_ecvt_s –** interpretuje *počet* jako celkový počet číslic ve výstupním řetězci a **_fcvt_s –** interpretuje *počet* jako počet číslic za desetinné čárky.

V jazyce C++ je použití touto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit velikost vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** všechny verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// fcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_fcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 120000
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
