---
title: _makepath – _wmakepath – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20985ce09d301002e6db3164cc3e99f36b03717b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204901"
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Vytvořte název cesty z komponent. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_makepath_s – _wmakepath_s –](makepath-s-wmakepath-s.md).

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

*cesta* vyrovnávací paměť pro úplnou cestu.

*jednotky* písmenem (A, B a tak dál) obsahuje odpovídající jednotce požadované a volitelné koncové dvojtečka. **_makepath –** vloží dvojtečka automaticky složenou cestu Pokud není nalezena. Pokud *jednotky* je **NULL** nebo odkazuje na prázdný řetězec, zobrazí se v složeného žádné písmeno jednotky *cesta* řetězec.

*příkaz dir* obsahuje cestu adresáře, bez zahrnutí specifikátor jednotky nebo skutečného názvu souboru. Do adresy koncové lomítko je volitelný a lomítkem (/) ani zpětné lomítko (\\) nebo může být možné použít v jediném *dir* argument. Pokud žádného koncového lomítka (/ nebo \\) je zadán, je automaticky vložen. Pokud *dir* je **NULL** nebo odkazuje na prázdný řetězec, žádná cesta k adresáři se vloží do složeného *cesta* řetězec.

*%{fname/* obsahuje základní název souboru bez žádné přípony názvů souborů. Pokud *%{fname/* je **NULL** nebo odkazuje na prázdný řetězec, žádný název souboru se vloží do složeného *cesta* řetězec.

*ext* obsahuje skutečnou příponu souboru, s nebo bez úvodní tečky (.). **_makepath –** vloží období automaticky, pokud se nezobrazí v *ext*. Pokud *ext* je **NULL** nebo odkazuje na prázdný řetězec, bez přípony se vloží do složeného *cesta* řetězec.

## <a name="remarks"></a>Poznámky

**_Makepath –** funkce vytvoří řetězec složené cesty z jednotlivých komponent uložením výsledku v *cesta*. *Cesta* může obsahovat písmeno jednotky, cesta k adresáři, názvu souboru a přípony názvu souboru. **_wmakepath –** je verze širokého znaku **_makepath –**; argumenty, které mají **_wmakepath –** jsou širokoznaké řetězce. **_wmakepath –** a **_makepath –** se jinak chovají stejně.

**Poznámka k zabezpečení** použijte řetězec zakončený hodnotou null. Abyste předešli přetečení vyrovnávací paměti, řetězec zakončený hodnotou null nesmí překročit velikost *cesta* vyrovnávací paměti. **_makepath –** není jisté, že nepřekračuje délku řetězce složenou cestu **_MAX_PATH**. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath –**|**_makepath**|**_makepath**|**_wmakepath**|

*Cesta* argumentu musí odkazovat na prázdné vyrovnávací paměti dostatečně velký pro úplnou cestu. Složené *cesta* nesmí být větší než **_MAX_PATH** – konstanta, definovány v Stdlib.h.

Pokud se cesta **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Kromě toho **errno** je nastavena na **EINVAL**. **NULL** hodnoty jsou povoleny pro všechny ostatní parametry.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
