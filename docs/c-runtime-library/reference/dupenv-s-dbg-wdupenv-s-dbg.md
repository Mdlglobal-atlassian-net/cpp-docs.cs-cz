---
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
api_name:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: 6c61986184f93c6cf6e83b33f77dce2bd017cfae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937680"
---
# <a name="_dupenv_s_dbg-_wdupenv_s_dbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Získá hodnotu z aktuálního prostředí.  Verze [_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md) , které přidělují paměť s [_malloc_dbg](malloc-dbg.md) k poskytnutí dalších informací o ladění.

## <a name="syntax"></a>Syntaxe

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení hodnoty proměnné

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru nebo **hodnotu null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

Nula při úspěchu – chybový kód při selhání.

Tyto funkce ověřují své parametry; Pokud je *vyrovnávací paměť* nebo *název_proměnné* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

Pokud tyto funkce nemůžou přidělit dostatek paměti, nastaví *vyrovnávací paměť* na **hodnotu null** a *NumberOfElements* na 0 a vrátí **ENOMEM**.

## <a name="remarks"></a>Poznámky

Funkce **_dupenv_s_dbg** a **_wdupenv_s_dbg** jsou stejné jako **_dupenv_s** a **_wdupenv_s** s tím rozdílem, že pokud je definována **_DEBUG** , používají tyto funkce ladicí verzi [](malloc.md), [_malloc_dbg](malloc-dbg.md), pro přidělení paměti pro hodnotu proměnné prostředí. Informace o funkcích ladění pro **_malloc_dbg**najdete v tématu [_malloc_dbg](malloc-dbg.md).

Tyto funkce není nutné volat explicitně ve většině případů. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC**. Pokud je definována **_CRTDBG_MAP_ALLOC** , volání **_dupenv_s** a **_wdupenv_s** jsou přemapována na **_Dupenv_s_dbg** a **_Wdupenv_s_dbg**v uvedeném pořadí s *blockType* nastavenou na **_NORMAL_BLOCK**. Proto nemusíte tyto funkce volat explicitně, pokud nechcete označit bloky haldy jako **_CLIENT_BLOCK**. Další informace o typech bloků naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
