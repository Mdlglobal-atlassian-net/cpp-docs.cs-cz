---
title: _makepath, _wmakepath
ms.date: 11/04/2016
api_name:
- _makepath
- _wmakepath
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: aafde0aeeebb7b773d3f96ca66ae65762dcdebdf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952931"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

Vytvořte název cesty z komponent. K dispozici jsou bezpečnější verze těchto funkcí; viz [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="syntax"></a>Syntaxe

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Vyrovnávací paměť úplné cesty.

*drive*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotce a volitelné koncové čárky. **_makepath** vloží dvojtečku do složené cesty automaticky, pokud chybí. Pokud má jednotka **hodnotu null** nebo odkazuje na prázdný řetězec, v řetězci složené *cesty* se nezobrazí žádné písmeno jednotky.

*dir*<br/>
Obsahuje cestu k adresářům, včetně označení jednotky nebo samotného názvu souboru. Koncové lomítko je nepovinné a v jednom argumentu *dir* se může použít lomítko (/) nebo\\zpětné lomítko () nebo obojí. Pokud není zadáno žádné koncové lomítko ( \\/nebo), je vloženo automaticky. Pokud je adresář **null** nebo odkazuje na prázdný řetězec, do řetězce složené *cesty* není vložena žádná cesta k adresáři.

*fname*<br/>
Obsahuje základní název souboru bez přípony názvu souboru. Pokud má fname **hodnotu null** nebo odkazuje na prázdný řetězec, do řetězce složené *cesty* není vložen žádný název souboru.

*ext*<br/>
Obsahuje skutečnou příponu názvu souboru s úvodním nebo Bezm počátečního období (.). **_makepath** Vloží tečku automaticky, pokud se nezobrazí v *EXT*. Pokud má EXT **hodnotu null** nebo odkazuje na prázdný řetězec, v řetězci složené *cesty* není vloženo žádné rozšíření.

## <a name="remarks"></a>Poznámky

Funkce **_makepath** vytvoří řetězec složených cest z jednotlivých komponent a uloží výsledek do *cesty*. *Cesta* může obsahovat písmeno jednotky, cestu k adresáři, název souboru a příponu názvu souboru. **_wmakepath** je **_makepath**verze s velkým znakem; argumenty **_wmakepath** jsou řetězce s libovolným znakem. **_wmakepath** a **_makepath** se chovají stejně jinak.

**Poznámka k zabezpečení** Použijte řetězec zakončený hodnotou null. Aby nedošlo k přetečení vyrovnávací paměti, řetězec zakončený hodnotou null nesmí být větší než velikost vyrovnávací paměti pro *cestu* . **_makepath** nezajistí, že délka řetězce složené cesty nepřekračuje **_MAX_PATH**. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Argument *cesty* musí ukazovat na prázdnou vyrovnávací paměť, která je dostatečně velká pro uložení úplné cesty. Složená *cesta* nesmí být větší než **_MAX_PATH** konstanta definovaná v Stdlib. h.

Pokud má cesta **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Kromě toho je **errno** nastaveno na **EINVAL**. Pro všechny ostatní parametry jsou povoleny hodnoty **null** .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
