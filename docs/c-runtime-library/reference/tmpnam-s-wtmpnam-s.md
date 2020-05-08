---
title: tmpnam_s, _wtmpnam_s
ms.date: 4/2/2020
api_name:
- tmpnam_s
- _wtmpnam_s
- _o__wtmpnam_s
- _o_tmpnam_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: 4839cb6baae8f163ac5e5efd8fecfab43f599d19
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917490"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

Vygenerujte názvy, které můžete použít k vytvoření dočasných souborů. Jedná se o verze [tmpnam a _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ukazatel, který bude obsahovat vygenerovaný název.

*sizeInChars*<br/>
Velikost vyrovnávací paměti ve znacích.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí 0, pokud bylo úspěšné, nebo číslo chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Návratová hodnota**|**Obsah**  *str*|
|**PLATNOST**|jakýmikoli|**EINVAL**|Neupraveno|
|není **null** (ukazuje na platnou paměť)|moc krátký|**ERANGE**|Neupraveno|

Pokud je parametr *str* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vrací název souboru, který aktuálně neexistuje. **tmpnam_s** vrátí název jedinečný v určeném dočasném adresáři Windows vráceném funkcí [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). Všimněte si, že pokud je název souboru před označené jako nedokončené zpětným lomítkem a žádné informace o cestě, jako je například \fname21, znamená to, že název je platný pro aktuální pracovní adresář.

V případě **tmpnam_s**můžete tento vygenerovaný název souboru Uložit do *str*. Maximální délka řetězce vráceného funkcí **tmpnam_s** je **L_TMPNAM_S**definována v stdio. Y. Pokud *str* má str **hodnotu NULL**, pak **tmpnam_s** ponechá výsledek v interní statické vyrovnávací paměti. Proto jakákoli následná volání zničí tuto hodnotu. Název generovaný **tmpnam_s** se skládá z programu generovaného programem a po prvním volání **tmpnam_s**je přípona souboru sekvenčních čísel v základní 32 (. 1-. 1vvvvvu, když **TMP_MAX_S** v stdio. H je **INT_MAX**).

**tmpnam_s** automaticky zpracovává argumenty vícebajtových znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle znakové stránky OEM získané z operačního systému. **_wtmpnam_s** je verze **tmpnam_s**s velkým znakem; argument a návratová hodnota **_wtmpnam_s** jsou řetězce s velkým počtem znaků. **_wtmpnam_s** a **tmpnam_s** se chovají stejně, s výjimkou toho, že **_wtmpnam_s** zpracovává řetězce vícebajtových znaků.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpnam_s**|\<stdio. h>|
|**_wtmpnam_s**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
