---
title: _gcvt_s – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60f68507f25ba6255b1c6a439c5e74729d2a2646
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="gcvts"></a>_gcvt_s

Převede hodnotu s plovoucí desetinnou čárkou na řetězec. Toto je verze [_gcvt –](gcvt.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vyrovnávací paměť pro uložení výsledek převodu.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti.

*value*<br/>
Hodnota má být převeden.

*číslice*<br/>
Počet platných číslic, které jsou uložené.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatný parametr (v následující tabulce najdete neplatné hodnoty), obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, je vrácena kód chyby. Kódy chyb jsou definovány v Errno.h. Seznam těchto chybách naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*sizeInBytes*|*value*|*číslice*|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|-------------------|-------------|--------------|------------|-----------------------|
|**HODNOTU NULL**|všechny|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|nula|všechny|všechny|**EINVAL –**|Nedojde ke změně.|
|Není **NULL** (odkazuje na platný paměti)|všechny|všechny|>= *sizeInBytes*|**EINVAL –**|Nedojde ke změně.|

**Problémy se zabezpečením**

**_gcvt_s –** může vygenerovat porušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**.

## <a name="remarks"></a>Poznámky

**_Gcvt_s –** funkce převede s plovoucí desetinnou čárkou *hodnotu* na řetězec znaků (která zahrnuje desetinné čárky a možné přihlašovací bajtů) a ukládá řetězec v *vyrovnávací paměti* . *vyrovnávací paměť* by měl být dostatečně velký na to, aby dokázala pojmout převedená hodnota plus ukončující prázdný znak, který se automaticky připojí. Vyrovnávací paměť délky **_CVTBUFSIZE** je dostatečná pro všechny plovoucí bodu hodnotu. Pokud velikost vyrovnávací paměti *číslic* + 1 se používá, funkce nepřepíše do konce vyrovnávací paměti, takže je nutné zadat dostatečná vyrovnávací paměti pro tuto operaci. **_gcvt_s –** pokusí vytvořit *číslic* číslic ve formátu desetinného čísla. Pokud ne, vyvolá *číslic* číslic v exponenciálním formátu. Koncové nuly lze potlačit v převodu.

V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze této funkce nejprve doplní vyrovnávací paměti s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_gcvt_s**|\<stdlib.h>|\<Error.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt_s](ecvt-s.md)<br/>
[_fcvt_s](fcvt-s.md)<br/>
[_gcvt](gcvt.md)<br/>
