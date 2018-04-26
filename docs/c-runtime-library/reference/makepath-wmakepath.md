---
title: _makepath –, _wmakepath – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6ad1331021331e9c9ddc1d1344aae8ed164ce2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Z komponenty vytvořte název cesty. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_makepath_s –, _wmakepath_s –](makepath-s-wmakepath-s.md).

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

*cesta* úplná cesta vyrovnávací paměti.

*jednotka* obsahuje písmeno (A, B a tak dále) odpovídající požadované jednotky a volitelné koncové dvojtečkou. **_makepath –** vloží dvojtečkou automaticky složené cesta Pokud není nalezena. Pokud *jednotky* je **NULL** nebo odkazuje na prázdný řetězec, se zobrazí v složené žádné písmeno jednotky *cesta* řetězec.

*dir* obsahuje cestu adresáře není včetně označení jednotky nebo název skutečného souboru. Do adresy koncové lomítko je volitelná a buď lomítkem (/) ani zpětné lomítko (\\) nebo obě může být použit v jedné *dir* argument. Pokud žádné koncové lomítko (/ nebo \\) je zadána, je-li vložit automaticky. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, neexistuje žádná cesta adresáře je vložen do složeného *cesta* řetězec.

*%{fname/* obsahuje název základního souboru bez žádné přípony názvů souborů. Pokud *%{fname/* je **NULL** nebo odkazuje na prázdný řetězec, žádný název souboru je vložen do složeného *cesta* řetězec.

*ext* obsahuje příponu názvu souboru skutečný, s nebo bez úvodní tečky (.). **_makepath –** vloží období automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, bez přípony se vloží do složeného *cesta* řetězec.

## <a name="remarks"></a>Poznámky

**_Makepath –** funkce vytvoří řetězec složené cesty z jednotlivých součástí, ukládání výsledků v *cestu*. *Cesta* může obsahovat písmeno jednotky, cesta k adresáři, název souboru a příponu názvu souboru. **_wmakepath –** je verze široká charakterová **_makepath –**; argumenty, které mají **_wmakepath –** jsou široká charakterová řetězce. **_wmakepath –** a **_makepath –** chovat jinak shodně.

**Poznámka k zabezpečení** pomocí řetězce ukončené hodnotou null. Abyste se vyhnuli přetečení vyrovnávací paměti, řetězce ukončené hodnotou null nesmí překročit velikost *cesta* vyrovnávací paměti. **_makepath –** není zajistí, že délka řetězec složené cesty **_max_path –**. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath –**|**_makepath**|**_makepath**|**_wmakepath**|

*Cesta* argument musí ukazovat na prázdnou dostatečně velký pro uložení úplná cesta vyrovnávací paměti. Složené *cesta* musí být větší než **_max_path –** konstanta, definované v Stdlib.h.

Pokud se cesta **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Kromě toho **errno** je nastaven na **einval –**. **NULL** hodnoty jsou povolené pro všechny ostatní parametry.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
