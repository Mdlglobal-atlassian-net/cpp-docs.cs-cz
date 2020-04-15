---
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341605"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Vytvoří název cesty z komponent. Jedná se o verze [_makepath, _wmakepath](makepath-wmakepath.md) s vylepšeními zabezpečení popsanými v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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

*Cestu*<br/>
Úplná vyrovnávací paměť cesty.

*sizeInWords*<br/>
Velikost vyrovnávací paměti ve slovech.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtů.

*Jednotky*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotce a volitelné koncové dvojtečky. **_makepath_s** vloží dvojtečku automaticky do složené cesty, pokud chybí. Pokud je *jednotka* **NULL** nebo odkazuje na prázdný řetězec, nezobrazí se v řetězci složené *cesty* žádné písmeno jednotky.

*Dir*<br/>
Obsahuje cestu adresářů, bez označení jednotky nebo skutečného názvu souboru. Koncové lomítko je volitelné a v jednom argumentu\\ *dir* může být použito lomítko (/) nebo zpětné lomítko ( ) nebo obojí. Pokud není zadáno žádné \\koncové lomítko (/ nebo ) , je vloženo automaticky. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, žádná cesta adresáře je vložen a složený řetězec *cesty.*

*Fname*<br/>
Obsahuje název základního souboru bez přípon názvů souborů. Pokud *je název null* nebo odkazuje na prázdný řetězec, není do řetězce složené *cesty* vložen žádný název souboru. **NULL**

*Ext*<br/>
Obsahuje vlastní příponu názvu souboru, s nebo bez úvodní tečky (.). **_makepath_s** vloží tečku automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, žádné rozšíření je vložen a složený řetězec *cesty.*

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*Cestu*|*sizeInWords* / *sizeInBytes*|Vrátit|Obsah *cesty*|
|------------|------------------------------------|------------|------------------------|
|**Null**|jakékoli|**EINVAL**|nezměněno|
|jakékoli|<= 0|**EINVAL**|nezměněno|

Pokud dojde k některéz výše uvedených chybových stavů, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**. **Null** je povoleno pro parametry *jednotky*, *fname*a *ext*. Informace o chování, pokud jsou tyto parametry null ukazatele nebo prázdné řetězce, naleznete v části Poznámky.

## <a name="remarks"></a>Poznámky

Funkce **_makepath_s** vytvoří složený řetězec cesty z jednotlivých součástí a výsledek uvede do *cesty*. *Cesta* může obsahovat písmeno jednotky, cestu k adresáři, název souboru a příponu názvu souboru. **_wmakepath_s** je širokoznaková verze **_makepath_s**; argumenty, které **mají _wmakepath_s** jsou řetězce širokých znaků. **_wmakepath_s** a **_makepath_s** se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Argument *cesty* musí ukazovat na prázdnou vyrovnávací paměť dostatečně velkou, aby byla celá cesta uložena. Složená *cesta* nesmí být větší než **konstanta _MAX_PATH** definovaná v souboru Stdlib.h.

Pokud je cesta **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Kromě toho je **errno** nastaveno na **EINVAL**. **Hodnoty NULL** jsou povoleny pro všechny ostatní parametry.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
