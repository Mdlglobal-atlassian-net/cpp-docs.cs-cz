---
title: _ecvt_s
ms.date: 04/05/2018
apiname:
- _ecvt_s
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
- ecvt_s
- _ecvt_s
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
ms.openlocfilehash: 0123c618eb5ba614bd8e5b5b3f1f4b0aff539c4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435578"
---
# <a name="ecvts"></a>_ecvt_s

Převede **double** číslo na řetězec. Toto je verze [_ecvt –](ecvt.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ecvt_s(
   char * _Buffer,
   size_t _SizeInBytes,
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
);
template <size_t size>
errno_t _ecvt_s(
   char (&_Buffer)[size],
   double _Value,
   int _Count,
   int *_Dec,
   int *_Sign
); // C++ only
```

### <a name="parameters"></a>Parametry

*_Buffer*<br/>
Naplní se ukazatel na řetězec číslic, výsledku převodu.

*_SizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*_Value*<br/>
Číslo, které má být převeden.

*_Count*<br/>
Počet číslic, které jsou uložené.

*_Dec*<br/>
Pozice uložené desetinné čárky.

*_Přihlásit*<br/>
Znak převedený čísla.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

V případě neplatného parametru, jak je uvedeno v následující tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **EINVAL**.

### <a name="error-conditions"></a>Chybové podmínky

|*_Buffer*|*_SizeInBytes*|_Value|_Count|_Dec|_Přihlásit|Návratová hodnota|Hodnota v *vyrovnávací paměti*|
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|
|**HODNOTU NULL**|Všechny|Všechny|Všechny|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|<=0|Všechny|Všechny|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Všechny|Všechny|Všechny|Všechny|**HODNOTU NULL**|Všechny|**EINVAL**|Nedojde ke změně.|
|Všechny|Všechny|Všechny|Všechny|Všechny|**HODNOTU NULL**|**EINVAL**|Nedojde ke změně.|

## <a name="security-issues"></a>Problémy se zabezpečením

**_ecvt_s –** může vygenerovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Ecvt_s –** funkce převede číslo s plovoucí desetinnou čárkou na řetězec znaků. *_Value* parametru je číslo s plovoucí desetinnou čárkou má být převeden. Tato funkce ukládá až *počet* číslic *_Value* jako řetězec a připojí znak null ('\0'). Pokud počet číslic v *_Value* překračuje *_Count*, poloměr zaoblení číslice nižšího řádu. Pokud jsou kratší než *počet* číslic, řetězec je doplněny nulami.

Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko *_Value* můžete získat *_Dec* a *podep_sat* po volání. *_Dec* parametr odkazuje na celočíselnou hodnotu poskytuje pozici od desetinné čárky s ohledem na začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, že desetinné čárky je nalevo od první číslice. *Podep_sat* parametr odkazuje na celé číslo označující znaménko převedený číslo. Pokud je hodnota celého čísla 0, je kladné číslo. V opačném případě je číslo záporné.

Vyrovnávací paměť o délce **_CVTBUFSIZE** je dostačující pro libovolnou hodnotu s plovoucí desetinnou čárkou.

Rozdíl mezi **_ecvt_s –** a **_fcvt_s –** probíhá vyhodnocení *_Count* parametru. **_ecvt_s –** interpretuje *_Count* jako celkový počet číslic ve výstupním řetězci, zatímco **_fcvt_s –** interpretuje *_Count* jako počet číslic za desetinné čárky.

V jazyce C++ je použití touto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit velikost vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|--------------|---------------------|---------------------|
|**_ecvt_s**|\<stdlib.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// ecvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( )
{
    char * buf = 0;
    int decimal;
    int sign;
    int err;

    buf = (char*) malloc(_CVTBUFSIZE);
    err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);

    if (err != 0)
    {
        printf("_ecvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 12000
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt_s](gcvt-s.md)<br/>
