---
title: _makepath_s –, _wmakepath_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eecae2f0b3b8e3ee81fe83fa3041b81ca219f334
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s

Název cesty vytvoří z komponenty. Toto jsou verze [_makepath –, _wmakepath –](makepath-wmakepath.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Velikost vyrovnávací paměti v slova.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*Jednotka*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotky a volitelné koncové dvojtečkou. **_makepath_s –** vloží dvojtečkou automaticky složené cesta Pokud není nalezena. Pokud *jednotky* je **NULL** nebo odkazuje na prázdný řetězec, se zobrazí v složené žádné písmeno jednotky *cesta* řetězec.

*Dir*<br/>
Obsahuje cestu adresáře není včetně označení jednotky nebo název skutečného souboru. Do adresy koncové lomítko je volitelná a buď lomítkem (/) ani zpětné lomítko (\\) nebo obě může být použit v jedné *dir* argument. Pokud žádné koncové lomítko (/ nebo \\) je zadána, je-li vložit automaticky. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, neexistuje žádná cesta adresáře je vložen do složeného *cesta* řetězec.

*%{fname/*<br/>
Obsahuje název základního souboru bez žádné přípony názvů souborů. Pokud *%{fname/* je **NULL** nebo odkazuje na prázdný řetězec, žádný název souboru je vložen do složeného *cesta* řetězec.

*ext*<br/>
Obsahuje příponu názvu souboru skutečný, s nebo bez úvodní tečky (.). **_makepath_s –** vloží období automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, bez přípony se vloží do složeného *cesta* řetězec.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšného; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*Cesta*|*sizeInWords* / *sizeInBytes*|Vrátí|Obsah *cesta*|
|------------|------------------------------------|------------|------------------------|
|**HODNOTU NULL**|všechny|**EINVAL –**|nedojde ke změně|
|všechny|<= 0|**EINVAL –**|nedojde ke změně|

Pokud dojde k některé z výše uvedených podmínek chyba, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a vrátí funkce **einval –**. **NULL** je povolen pro parametry *jednotky*, *%{fname/*, a *ext*. Informace o chování při tyto parametry jsou ukazatelé s hodnotou null nebo prázdné řetězce, najdete v části poznámky.

## <a name="remarks"></a>Poznámky

**_Makepath_s –** funkce vytvoří řetězec složené cesty z jednotlivých součástí, ukládání výsledků v *cestu*. *Cesta* může obsahovat písmeno jednotky, cesta k adresáři, název souboru a příponu názvu souboru. **_wmakepath_s –** je verze široká charakterová **_makepath_s –**; argumenty, které mají **_wmakepath_s –** jsou široká charakterová řetězce. **_wmakepath_s –** a **_makepath_s –** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*Cesta* argument musí ukazovat na prázdnou dostatečně velký pro uložení úplná cesta vyrovnávací paměti. Složené *cesta* musí být větší než **_max_path –** konstanta, definované v Stdlib.h.

Pokud se cesta **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Kromě toho **errno** je nastaven na **einval –**. **NULL** hodnoty jsou povolené pro všechny ostatní parametry.

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
