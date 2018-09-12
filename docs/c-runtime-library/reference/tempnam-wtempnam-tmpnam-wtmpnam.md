---
title: _tempnam – _wtempnam –, tmpnam – _wtmpnam – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdd853affc343a4f07c64d025cd73122fdb8d458
ms.sourcegitcommit: 32fd693d092ea0b43c3916703364f494a5b502cf
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389481"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Generovat názvy, které lze použít k vytvoření dočasné soubory. Bezpečnější verze některých z těchto funkcí jsou k dispozici. Zobrazit [tmpnam_s – _wtmpnam_s –](tmpnam-s-wtmpnam-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>Parametry

*prefix*<br/>
Řetězec, který bude pre čekajícího na názvy vrácené **_tempnam –**.

*adresář*<br/>
Cesta v názvu souboru používá, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.

*str*<br/>
Ukazatel, který se uloží vygenerovaný název a bude stejný jako název vrácené funkcí. Je to pohodlný způsob, jak uložit vygenerovaný název.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na název generované nebo **NULL** Pokud dojde k selhání. Selhání může dojít, pokud při pokusu o více než **TMP_MAX** (viz STDIO. H) volání s **tmpnam –** nebo pokud používáte **_tempnam –** a je neplatný název adresáře zadané v proměnné prostředí TMP a v *dir* parametru.

> [!NOTE]
> Ukazatele vrácené **tmpnam –** a **_wtmpnam –** přejděte na interní statické vyrovnávací paměti. [bezplatné](free.md) by neměla být volána k uvolnění těchto ukazatelů. **bezplatné** musí být volána pro ukazatele přidělaná **_tempnam –** a **_wtempnam –**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí vrací název souboru, který ještě neexistuje. **tmpnam –** vrací název, který je jedinečný v určené dočasný adresář Windows vrácený [GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw). **\_tempnam –** generuje jedinečný název v adresáři než na kterém určené. Všimněte si, než když název souboru je pre čekajícího zpětným lomítkem a informace o cestě, jako je například \fname21, to znamená, že název je platný pro aktuální pracovní adresář. 

Pro **tmpnam –**, můžete uložit tento název generovaného souboru v *str*. Pokud *str* je **NULL**, pak **tmpnam –** ponechá výsledek v interní statické vyrovnávací paměti. Proto následných volání zničit tuto hodnotu. Název generované **tmpnam –** se skládá z názvu souboru generovaného programu a po prvním volání **tmpnam –**, příponu souboru pořadová čísla v základní 32 (.1 .vvu, když **TMP_MAX**  v STDIO. H je 32 767.)

**_tempnam –** bude generovat jedinečný název souboru pro adresář zvolena podle následujících pravidel:

- Pokud proměnná prostředí TMP definované a je nastavena na platný název adresáře, vygeneruje se pro adresář zadaný TMP jedinečné názvy souborů.

- Pokud není definována proměnná prostředí TMP, nebo pokud je nastavena na název adresáře, který neexistuje, **_tempnam –** použije *dir* parametr cesty, pro který vygeneruje jedinečné názvy.

- Pokud není definována proměnná prostředí TMP nebo pokud je nastavena na název adresáře, který neexistuje a pokud *dir* je buď **NULL** nebo nastavte na název adresáře, který neexistuje, **_ tempnam –** aktuálního pracovního adresáře použije k vygenerování jedinečné názvy. V současné době Pokud oba TMP a *dir* zadání názvů adresářů, které neexistují, **_tempnam –** volání funkce se nezdaří.

Jméno vrácené funkcí **_tempnam –** bude zřetězení *předponu* a pořadové číslo, které se dá vytvořit jedinečný název souboru pro zadaný adresář. **_tempnam –** vygeneruje názvy souborů, které mají bez přípony. **_tempnam –** používá [malloc](malloc.md) k přidělení místa pro název souboru; program je zodpovědná za uvolnění místa na tento, pokud už je nepotřebujete.

**_tempnam –** a **tmpnam –** automaticky popisovač vícebajtového znaku zakončeného argumenty řetězce podle potřeby, rozpozná vícebajtové znakové sekvence podle znakovou stránku OEM získané z operačního systému. **_wtempnam –** je verze širokého znaku **_tempnam –**; argumenty a vrácené hodnoty **_wtempnam –** jsou širokoznaké řetězce. **_wtempnam –** a **_tempnam –** chovají stejně, s výjimkou, že **_wtempnam –** nezpracovává vícebajtové znakové řetězce. **_wtmpnam –** je verze širokého znaku **tmpnam –**; argument a návratová hodnota funkce **_wtmpnam –** jsou širokoznaké řetězce. **_wtmpnam –** a **tmpnam –** chovají stejně, s výjimkou, že **_wtmpnam –** nezpracovává vícebajtové znakové řetězce.

Pokud **_DEBUG** a **_CRTDBG_MAP_ALLOC** jsou definovány, **_tempnam –** a **_wtempnam –** jsou nahrazena voláními funkcí [_tempnam – _dbg a _wtempnam_dbg –](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam –**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam –**, **_wtmpnam –**|\<stdio.h > nebo \<wchar.h >|
|**tmpnam**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
