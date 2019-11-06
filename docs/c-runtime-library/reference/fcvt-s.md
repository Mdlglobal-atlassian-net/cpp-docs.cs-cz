---
title: _fcvt_s
ms.date: 04/05/2018
api_name:
- _fcvt_s
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
- fcvt_s
- _fcvt_s
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
ms.openlocfilehash: a7dcb9b7acc462d9570ee2cb7adb0dbd06df77c9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623838"
---
# <a name="_fcvt_s"></a>_fcvt_s

Převede číslo s plovoucí desetinnou čárkou na řetězec. Jedná se o verzi [_fcvt](fcvt.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Poskytnutá vyrovnávací paměť, která bude obsahovat výsledek převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*value*<br/>
Číslo, které má být převedeno.

*výpočtu*<br/>
Počet číslic za desetinnou čárkou.

*18.12*<br/>
Ukazatel na uloženou pozici desetinných míst.

*sign*<br/>
Ukazatel na uložený indikátor znaménka.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v errno. h. Seznam těchto chyb naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru, jak je uvedeno v následující tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*sizeInBytes*|value|count|dec|znak|Vrátit|Hodnota v *bufferu*|
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|
|**PLATNOST**|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Není **null** (ukazuje na platnou paměť)|< = 0|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|Nezměněno.|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**PLATNOST**|Jakýmikoli|**EINVAL**|Nezměněno.|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**PLATNOST**|**EINVAL**|Nezměněno.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_fcvt_s** může vygenerovat porušení přístupu, pokud *vyrovnávací paměť* neukazuje na platnou paměť a není **null**.

## <a name="remarks"></a>Poznámky

Funkce **_fcvt_s** převede číslo s plovoucí desetinnou čárkou na řetězec znaků zakončený hodnotou null. Parametr *Value* je číslo s plovoucí desetinnou čárkou, které má být převedeno. **_fcvt_s** ukládá číslice *hodnoty* jako řetězec a připojí znak null (' \ 0 '). Parametr *Count* určuje počet číslic, které mají být uloženy za desetinnou čárkou. Nadbytečné číslice se zaokrouhlují na *počty* míst. Pokud je k dispozici *méně než číslice* typu přesnosti, je řetězec doplněn nulami.

V řetězci jsou uloženy pouze číslice. Pozice desetinné čárky a znaménko *hodnoty* lze získat z *dec* a *podepsat* po volání. Parametr *dec* odkazuje na celočíselnou hodnotu; Tato celočíselná hodnota udává pozici desetinné čárky vůči začátku řetězce. Nula nebo záporná celočíselná hodnota značí, že desetinná čárka leží vlevo od první číslice. *Symbol* parametru odkazuje na celé číslo označující znaménko *hodnoty*. Celé číslo je nastavené na 0, pokud je *hodnota* kladná a je nastavená na nenulové číslo, pokud je *hodnota* záporná.

Vyrovnávací paměť s délkou **_CVTBUFSIZE** je dostačující pro všechny hodnoty s plovoucí desetinnou čárkou.

Rozdíl mezi **_ecvt_s** a **_fcvt_s** je ve výkladu parametru *Count* . **_ecvt_s** interpretuje *počítání* jako celkový počet číslic ve výstupním řetězci a **_fcvt_s** interpretuje *počet číslic* za desetinnou čárkou.

V C++systému je použití této funkce zjednodušené přetížením šablony; přetížení může odvodit délku vyrovnávací paměti automaticky a eliminuje nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve vyplní vyrovnávací paměť pomocí 0xFE. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_fcvt_s**|\<Stdlib. h >|\<errno. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovny:** Všechny verze [funkcí knihovny CRT](../../c-runtime-library/crt-library-features.md).

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
