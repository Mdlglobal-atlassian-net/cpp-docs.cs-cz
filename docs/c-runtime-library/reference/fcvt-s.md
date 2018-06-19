---
title: _fcvt_s – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2897c199b1b7022de8d5735c4da5f02d7627a418
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404058"
---
# <a name="fcvts"></a>_fcvt_s

Převede dvě desetinná čísla na řetězec. Toto je verze [_fcvt –](fcvt.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Poskytnutá vyrovnávací paměti, kterou bude obsahovat výsledek převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*value*<br/>
Číslo, které má být převeden.

*Počet*<br/>
Počet číslic za desetinnou čárkou.

*DEC*<br/>
Ukazatel na uložené pozici desetinné čárky.

*sign*<br/>
Ukazatel na uložené přihlašovací indikátoru.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Seznam těchto chybách naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatný parametr, jak je uvedeno v následující tabulce, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*sizeInBytes*|value|count|dec|znak|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**HODNOTU NULL**|všechny|všechny|všechny|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|<=0|všechny|všechny|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|všechny|všechny|všechny|všechny|**HODNOTU NULL**|všechny|**EINVAL –**|Nedojde ke změně.|
|všechny|všechny|všechny|všechny|všechny|**HODNOTU NULL**|**EINVAL –**|Nedojde ke změně.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_fcvt_s –** může generovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Fcvt_s –** funkce převede dvě desetinná čísla na řetězec znaků ukončený hodnotou null. *Hodnotu* parametr je číslo s plovoucí desetinnou čárkou má být převeden. **_fcvt_s –** ukládá číslice z *hodnotu* jako řetězec a připojí znak hodnoty null ('\0'). *Počet* parametr určuje počet číslic ukládaly za desetinnou čárkou. Jsou nadbytečné číslic zaokrouhlen *počet* umístí. Pokud máte méně než *počet* platných číslic, řetězec je doplněno nulami.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *hodnotu* lze získat z *dec* a *přihlašovací* po volání. *Dec* parametr odkazuje na celočíselnou hodnotu; uvádí tato hodnota celé číslo pozice od desetinné čárky s ohledem na začátku řetězce. Nula nebo záporná celočíselná hodnota označuje, zda desetinné čárky je nalevo od první číslice. Parametr *přihlašovací* odkazuje na celé číslo udávající znaménko *hodnotu*. Celé číslo nastavena na 0, pokud *hodnotu* kladné a je nastavená na nenulové číslo Pokud *hodnota* je záporná.

Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro všechny plovoucí bodu hodnotu.

Rozdíl mezi **_ecvt_s –** a **_fcvt_s –** je při interpretaci *počet* parametr. **_ecvt_s –** interpretuje *počet* jako celkový počet číslic do výstupního řetězce a **_fcvt_s –** interpretuje *počet* jako počet číslic za desetinné čárky.

V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve doplní vyrovnávací paměti s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
[_fcvt](fcvt.md)<br/>
