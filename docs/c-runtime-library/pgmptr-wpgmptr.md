---
title: _pgmptr, _wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: beff0401d0aa2aa21819e58618ef4c02795d4393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300154"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr, _wpgmptr

Cesta ke spustitelnému souboru. Zastaralé použijte [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) a [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md).

## <a name="syntax"></a>Syntaxe

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>Poznámky

Když se program spustí z překladače příkazu (cmd. exe), `_pgmptr` se automaticky inicializuje na úplnou cestu ke spustitelnému souboru. Pokud je například Hello. exe v C:\BIN a C:\BIN je v cestě, `_pgmptr` je při spuštění nastaveno na C:\BIN\Hello.exe:

```
C> hello
```

Když se program nespustí z příkazového řádku, `_pgmptr` se může inicializovat do názvu programu (základní název souboru bez přípony názvu souboru) nebo do názvu souboru, relativní cesty nebo úplné cesty.

`_wpgmptr` je protějšek se všemi znaky `_pgmptr` pro použití s programy, které používají `wmain`.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>Požadavky

|Proměnná|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>Příklad

Následující program ukazuje použití `_pgmptr`.

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

Můžete použít `_wpgmptr` změnou `%Fs` na `%S` a `main` na `wmain`.

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)
