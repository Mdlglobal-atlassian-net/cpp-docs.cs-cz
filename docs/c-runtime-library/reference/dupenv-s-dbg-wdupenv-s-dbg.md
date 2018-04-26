---
title: _dupenv_s_dbg –, _wdupenv_s_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc6aa566770bd8b2e12cefac22c414fd4c43a118
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Získání hodnoty z aktuální prostředí.  Verze [_dupenv_s –, _wdupenv_s –](dupenv-s-wdupenv-s.md) , přidělit paměť s [_malloc_dbg –](malloc-dbg.md) poskytnout další informace o ladění.

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
Vyrovnávací paměť pro uložení hodnota proměnné.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí.

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

Tyto funkce ověřit jejich parametrů; Pokud *vyrovnávací paměti* nebo *název_proměnné* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, nastavte funkce **errno** k **einval –** a vrátit **einval –**.

Pokud tyto funkce nemůže přidělit dostatek paměti, nastavují *vyrovnávací paměti* k **NULL** a *numberOfElements* 0, a vrátí **enomem –**.

## <a name="remarks"></a>Poznámky

**_Dupenv_s_dbg –** a **_wdupenv_s_dbg –** funkce jsou stejné jako **_dupenv_s –** a **_wdupenv_s –** s tím rozdílem, že když **_DEBUG –** je definován, tyto funkce používají verzi ladění [malloc –](malloc.md), [_malloc_dbg –](malloc-dbg.md), přidělit paměť pro hodnotu proměnné prostředí. Informace o ladění funkce **_malloc_dbg –**, najdete v části [_malloc_dbg –](malloc-dbg.md).

Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat příznak **_crtdbg_map_alloc –**. Když **_crtdbg_map_alloc –** je definován, volání **_dupenv_s –** a **_wdupenv_s –** jsou mapovány na **_dupenv_s_dbg –** a **_wdupenv_s_dbg –**, s *blockType* nastavena na **_normal_block –**. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako **_client_block –**. Další informace o typech bloku, najdete v části [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg –**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
