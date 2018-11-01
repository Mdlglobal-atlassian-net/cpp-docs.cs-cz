---
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
apitype: DLLExport
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
ms.openlocfilehash: 95d8c18a0ebc543304fdb6bf51c4adde589333aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579585"
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Získání hodnoty z aktuálního prostředí.  Verze [_dupenv_s – _wdupenv_s –](dupenv-s-wdupenv-s.md) , přidělení paměti s [_malloc_dbg](malloc-dbg.md) poskytnout další informace o ladění.

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

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro ukládání hodnotu proměnné.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí.

*blockType*<br/>
Požadovaný typ bloku paměti: **_CLIENT_BLOCK** nebo **_NORMAL_BLOCK**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; při selhání kód chyby.

Tyto funkce ověřují své parametry; Pokud *vyrovnávací paměti* nebo *název_proměnné* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

Pokud těmto funkcím nelze přidělit dostatek paměti, že nastavené *vyrovnávací paměti* k **NULL** a *numberOfElements* na 0 a vrátí **ENOMEM**.

## <a name="remarks"></a>Poznámky

**_Dupenv_s_dbg –** a **_wdupenv_s_dbg –** funkce jsou stejné jako **_dupenv_s –** a **_wdupenv_s –** s tím rozdílem, že když **_DEBUG** je definován, tyto funkce používají ladicí verze [malloc](malloc.md), [_malloc_dbg](malloc-dbg.md), přidělení paměti pro hodnotu proměnné prostředí. Informace o ladění funkcí **_malloc_dbg**, naleznete v tématu [_malloc_dbg](malloc-dbg.md).

Chcete-li explicitně volat tyto funkce ve většině případů nepotřebujete. Místo toho můžete definovat příznak **_CRTDBG_MAP_ALLOC**. Když **_CRTDBG_MAP_ALLOC** je definován, jsou volání **_dupenv_s –** a **_wdupenv_s –** budou přemapovány na **_dupenv_s_dbg –** a **_wdupenv_s_dbg –**, se *blockType* nastavena na **_NORMAL_BLOCK**. Proto není potřeba explicitně volat tyto funkce, pokud chcete označit jako bloky haldy **_CLIENT_BLOCK**. Další informace o typech bloku, naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg –**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
