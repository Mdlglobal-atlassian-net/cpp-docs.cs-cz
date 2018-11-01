---
title: _makepath_s, _wmakepath_s
ms.date: 11/04/2016
apiname:
- _wmakepath_s
- _makepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 6914299dd7ede97c9004dcc95e01b1a35188f5c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471913"
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s

Vytvoří název cesty z komponent. Jde o verzích [_makepath – _wmakepath –](makepath-wmakepath.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Úplná cesta vyrovnávací paměti.

*sizeInWords*<br/>
Velikost vyrovnávací paměti ve slovech.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*Jednotky*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající na požadovaný disk a volitelné koncové dvojtečka. **_makepath_s –** vloží dvojtečka automaticky složenou cestu Pokud není nalezena. Pokud *jednotky* je **NULL** nebo odkazuje na prázdný řetězec, zobrazí se v složeného žádné písmeno jednotky *cesta* řetězec.

*adresář*<br/>
Obsahuje cestu adresáře, bez zahrnutí specifikátor jednotky nebo skutečného názvu souboru. Do adresy koncové lomítko je volitelný a lomítkem (/) ani zpětné lomítko (\\) nebo může být možné použít v jediném *dir* argument. Pokud žádného koncového lomítka (/ nebo \\) je zadán, je automaticky vložen. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, žádná cesta k adresáři se vloží do složeného *cesta* řetězec.

*%{fname/*<br/>
Obsahuje základní název souboru bez žádné přípony názvů souborů. Pokud *%{fname/* je **NULL** nebo odkazuje na prázdný řetězec, žádný název souboru se vloží do složeného *cesta* řetězec.

*ext, přípona*<br/>
Obsahuje skutečnou příponu souboru, s nebo bez úvodní tečky (.). **_makepath_s –** vloží období automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, bez přípony se vloží do složeného *cesta* řetězec.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*Cesta*|*sizeInWords* / *sizeInBytes*|Vrátí|Obsah *cesta*|
|------------|------------------------------------|------------|------------------------|
|**HODNOTU NULL**|Všechny|**EINVAL**|Nezměněno|
|Všechny|<= 0|**EINVAL**|Nezměněno|

Pokud dojde k některé z výše uvedených chybové stavy, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**. **NULL** je povolený pro parametry *jednotky*, *%{fname/*, a *ext*. Informace o chování při tyto parametry jsou ukazatelé s hodnotou null nebo prázdné řetězce, naleznete v části poznámky.

## <a name="remarks"></a>Poznámky

**_Makepath_s –** funkce vytvoří řetězec složené cesty z jednotlivých komponent uložením výsledku v *cesta*. *Cesta* může obsahovat písmeno jednotky, cesta k adresáři, název souboru a příponu názvu souboru. **_wmakepath_s –** je verze širokého znaku **_makepath_s –**; argumenty, které mají **_wmakepath_s –** jsou širokoznaké řetězce. **_wmakepath_s –** a **_makepath_s –** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*Cesta* argumentu musí odkazovat na prázdné vyrovnávací paměti dostatečně velký pro úplnou cestu. Složené *cesta* nesmí být větší než **_MAX_PATH** – konstanta, definovány v Stdlib.h.

Pokud se cesta **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Kromě toho **errno** je nastavena na **EINVAL**. **NULL** hodnoty jsou povoleny pro všechny ostatní parametry.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
