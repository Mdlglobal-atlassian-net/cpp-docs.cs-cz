---
title: _makepath, _wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341582"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

Vytvořte název cesty z komponent. K dispozici jsou bezpečnější verze těchto funkcí. viz [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

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

*Cestu*<br/>
Úplná vyrovnávací paměť cesty.

*Jednotky*<br/>
Obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotce a volitelné koncové dvojtečky. **_makepath** vloží dvojtečku automaticky do složené cesty, pokud chybí. Pokud je *jednotka* **NULL** nebo odkazuje na prázdný řetězec, nezobrazí se v řetězci složené *cesty* žádné písmeno jednotky.

*Dir*<br/>
Obsahuje cestu adresářů, bez označení jednotky nebo skutečného názvu souboru. Koncové lomítko je volitelné a v jednom argumentu\\ *dir* může být použito lomítko (/) nebo zpětné lomítko ( ) nebo obojí. Pokud není zadáno žádné \\koncové lomítko (/ nebo ) , je vloženo automaticky. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, žádná cesta adresáře je vložen a složený řetězec *cesty.*

*Fname*<br/>
Obsahuje název základního souboru bez přípon názvů souborů. Pokud *je název null* nebo odkazuje na prázdný řetězec, není do řetězce složené *cesty* vložen žádný název souboru. **NULL**

*Ext*<br/>
Obsahuje vlastní příponu názvu souboru, s nebo bez úvodní tečky (.). **_makepath** vloží tečku automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, žádné rozšíření je vložen a složený řetězec *cesty.*

## <a name="remarks"></a>Poznámky

Funkce **_makepath** vytvoří složený řetězec cesty z jednotlivých součástí a uvede výsledek do *cesty*. *Cesta* může obsahovat písmeno jednotky, cestu k adresáři, název souboru a příponu názvu souboru. **_wmakepath** je širokoznaková verze **_makepath**; argumenty, které mají **_wmakepath,** jsou řetězce s širokými znaky. **_wmakepath** a **_makepath** se chovají stejně jinak.

**Poznámka k zabezpečení** Použijte řetězec s ukončeným hodnotou null. Aby nedošlo k přetečení vyrovnávací paměti, řetězec ukončený hodnotou null nesmí překročit velikost vyrovnávací paměti *cesty.* **_makepath** nezajišťuje, že délka řetězce složené cesty nepřekročí **_MAX_PATH**. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Argument *cesty* musí ukazovat na prázdnou vyrovnávací paměť dostatečně velkou, aby byla celá cesta uložena. Složená *cesta* nesmí být větší než **konstanta _MAX_PATH** definovaná v souboru Stdlib.h.

Pokud je cesta **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Kromě toho je **errno** nastaveno na **EINVAL**. **Hodnoty NULL** jsou povoleny pro všechny ostatní parametry.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
