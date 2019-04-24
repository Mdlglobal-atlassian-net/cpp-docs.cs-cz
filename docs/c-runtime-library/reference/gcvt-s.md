---
title: _gcvt_s
ms.date: 04/05/2018
apiname:
- _gcvt_s
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
- _gcvt_s
- gcvt_s
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
ms.openlocfilehash: 168e0657150d072bbe41cd0ad6e914ca1f53e512
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332291"
---
# <a name="gcvts"></a>_gcvt_s

Převede hodnotu s plovoucí desetinnou čárkou na řetězec. Toto je verze [_gcvt –](gcvt.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _gcvt_s(
   char *buffer,
   size_t sizeInBytes,
   double value,
   int digits
);
template <size_t cchStr>
errno_t _gcvt_s(
   char (&buffer)[cchStr],
   double value,
   int digits
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro ukládání výsledku převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti.

*value*<br/>
Hodnota k převedení.

*číslice*<br/>
Počet platných číslic, které jsou uložené.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatného parametru (viz následující tabulka neplatné hodnoty), je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí se kód chyby. Kódy chyb jsou definovány v Errno.h. Seznam těchto chyb, naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*sizeInBytes*|*value*|*číslice*|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**NULL**|Všechny|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|nula|Všechny|Všechny|**EINVAL**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|Všechny|Všechny|>= *sizeInBytes*|**EINVAL**|Nedojde ke změně.|

**Problémy se zabezpečením**

**_gcvt_s –** můžete vygenerovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Gcvt_s –** funkce převede plovoucí desetinné čárky *hodnotu* na řetězec znaků (která zahrnuje desetinné čárky a možné podepsat bajtů) a uloží řetězec v *vyrovnávací paměti* . *vyrovnávací paměť* by měl být dostatečně velký, aby odpovídala převedená hodnota plus ukončujícího znaku null, která se automaticky připojí. Vyrovnávací paměť o délce **_CVTBUFSIZE** je dostatečná pro všechny plovoucí desetinnou čárkou. Pokud vyrovnávací paměť o velikosti *číslic* + 1 se používá, funkci nepřepíše konce vyrovnávací paměti, takže je nutné poskytnout dostatek vyrovnávací paměti pro tuto operaci. **_gcvt_s –** pokusí vytvořit *číslic* číslic ve formátu desetinného čísla. V případě nedostupnosti vznikne *číslic* číslic v exponenciálním formátu. Koncové nuly jde potlačit v převodu.

V jazyce C++ je použití touto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit velikost vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<error.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gcvt_s.c
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main()
{
    char buf[_CVTBUFSIZE];
    int decimal;
    int sign;
    int err;

    err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);

    if (err != 0)
    {
        printf("_gcvt_s failed with error code %d\n", err);
        exit(1);
    }

    printf("Converted value: %s\n", buf);
}
```

```Output
Converted value: 1.2
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
