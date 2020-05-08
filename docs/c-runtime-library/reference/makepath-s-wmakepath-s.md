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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8eb3cf338d7486d7e7893090a1390e5d2d16a438
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914483"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Vytvoří název cesty z komponent. Jedná se o verze [_makepath, _wmakepath](makepath-wmakepath.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*dílčí*<br/>
Vyrovnávací paměť úplné cesty.

*sizeInWords*<br/>
Velikost vyrovnávací paměti ve slovech.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti v bajtech.

*disky*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotce a volitelné koncové čárky. Pokud chybí, **_makepath_s** vloží dvojtečku do složené cesty automaticky. Pokud *drive* má jednotka **hodnotu null** nebo odkazuje na prázdný řetězec, v řetězci složené *cesty* se nezobrazí žádné písmeno jednotky.

*Dir*<br/>
Obsahuje cestu k adresářům, včetně označení jednotky nebo samotného názvu souboru. Koncové lomítko je nepovinné a v jednom argumentu *dir* se může použít lomítko (/) nebo\\zpětné lomítko () nebo obojí. Pokud není zadáno žádné koncové lomítko ( \\/nebo), je vloženo automaticky. Pokud *dir* je adresář **null** nebo odkazuje na prázdný řetězec, do řetězce složené *cesty* není vložena žádná cesta k adresáři.

*fname*<br/>
Obsahuje základní název souboru bez přípony názvu souboru. Pokud *fname* má fname **hodnotu null** nebo odkazuje na prázdný řetězec, do řetězce složené *cesty* není vložen žádný název souboru.

*rozšířeného*<br/>
Obsahuje skutečnou příponu názvu souboru s úvodním nebo Bezm počátečního období (.). **_makepath_s** Vloží tečku automaticky, pokud se nezobrazí v *EXT*. Pokud *ext* má EXT **hodnotu null** nebo odkazuje na prázdný řetězec, v řetězci složené *cesty* není vloženo žádné rozšíření.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*dílčí*|*sizeInWords* / *sizeInBytes*|Vrátit|Obsah *cesty*|
|------------|------------------------------------|------------|------------------------|
|**PLATNOST**|jakýmikoli|**EINVAL**|Neupraveno|
|jakýmikoli|<= 0|**EINVAL**|Neupraveno|

Pokud dojde k některé z výše uvedených chybových podmínek, vyvolají tyto funkce obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EINVAL**. Pro *jednotky*Parameters, *fname*a *EXT*jsou povoleny **hodnoty null** . Informace o chování, když jsou tyto parametry ukazateli na hodnotu null nebo prázdné řetězce, naleznete v části poznámky.

## <a name="remarks"></a>Poznámky

Funkce **_makepath_s** vytváří řetězec složených cest z jednotlivých komponent a ukládá výsledek do *cesty*. *Cesta* může obsahovat písmeno jednotky, cestu k adresáři, název souboru a příponu názvu souboru. **_wmakepath_s** je verze **_makepath_s**s velkým znakem; argumenty **_wmakepath_s** jsou řetězce s libovolným znakem. **_wmakepath_s** a **_makepath_s** se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Argument *cesty* musí ukazovat na prázdnou vyrovnávací paměť, která je dostatečně velká pro uložení úplné cesty. Složená *cesta* nesmí být větší než **_MAX_PATH** konstanta definovaná v Stdlib. h.

Pokud má cesta **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Kromě toho je **errno** nastaveno na **EINVAL**. Pro všechny ostatní parametry jsou povoleny hodnoty **null** .

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. K zakázání tohoto chování použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath_s**|\<Stdlib. h>|
|**_wmakepath_s**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
