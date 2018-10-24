---
title: tmpnam_s – _wtmpnam_s – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c5272f662580eff92e9ec15860b978ab739e613
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691598"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s

Generovat názvy, které lze použít k vytvoření dočasné soubory. Jde o verzích [tmpnam – a _wtmpnam –](tempnam-wtempnam-tmpnam-wtmpnam.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel, který se uloží vygenerovaný název.

*sizeInChars*<br/>
Velikost vyrovnávací paměti ve znacích.

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí 0 v případě úspěchu nebo číslo chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Návratová hodnota**|**Obsah**  *str* |
|**HODNOTU NULL**|Všechny|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platný paměti)|příliš krátký|**ERANGE**|Nezměněno|

Pokud *str* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vrací název souboru, který ještě neexistuje. **tmpnam_s –** vrátí název jedinečný v určené dočasný adresář Windows vrácený [GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw). Všimněte si, než když název souboru je pre čekajícího zpětným lomítkem a informace o cestě, jako je například \fname21, to znamená, že název je platný pro aktuální pracovní adresář.

Pro **tmpnam_s –**, můžete uložit tento název generovaného souboru v *str*. Maximální délka řetězce vráceného **tmpnam_s –** je **L_tmpnam_s**definované v STDIO. H. Pokud *str* je **NULL**, pak **tmpnam_s –** ponechá výsledek v interní statické vyrovnávací paměti. Proto následných volání zničit tuto hodnotu. Název generované **tmpnam_s –** se skládá z názvu souboru generovaného programu a po prvním volání **tmpnam_s –**, příponu souboru pořadová čísla v základní 32 (.1 .1vvvvvu, když **TMP _MAX_S** v STDIO. H je **INT_MAX**).

**tmpnam_s –** automaticky zpracovává vícebajtového znaku zakončeného argumenty řetězce podle potřeby, rozpozná vícebajtové znakové sekvence podle znakovou stránku OEM získané z operačního systému. **_wtmpnam_s –** je verze širokého znaku **tmpnam_s –**; argument a návratová hodnota funkce **_wtmpnam_s –** jsou širokoznaké řetězce. **_wtmpnam_s –** a **tmpnam_s –** chovají stejně, s výjimkou, že **_wtmpnam_s –** nezpracovává vícebajtové znakové řetězce.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
