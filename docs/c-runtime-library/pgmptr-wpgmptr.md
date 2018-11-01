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
ms.openlocfilehash: c59134afc3b4d0f6360984c67dede28c27010bae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597528"
---
# <a name="pgmptr-wpgmptr"></a>_pgmptr, _wpgmptr

Cesta spustitelného souboru. Zastaralé; použít [_get_pgmptr –](../c-runtime-library/reference/get-pgmptr.md) a [_get_wpgmptr –](../c-runtime-library/reference/get-wpgmptr.md).

## <a name="syntax"></a>Syntaxe

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>Poznámky

Při spuštění programu ze překladač příkazů (Cmd.exe) `_pgmptr` je automaticky inicializován na úplnou cestu spustitelného souboru. Například pokud Hello.exe C:\BIN a C:\BIN je na cestě `_pgmptr` při spuštění nastavený na C:\BIN\Hello.exe:

```
C> hello
```

Pokud není program spustit z příkazového řádku `_pgmptr` může být inicializován, název aplikace (základní název pro souboru bez přípony názvu souboru) nebo název souboru, relativní cestu nebo úplnou cestu.

`_wpgmptr` je širokoznaká protějškem `_pgmptr` pro použití s programy, které používají `wmain`.

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

```
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

Můžete použít `_wpgmptr` změnou `%Fs` k `%S` a `main` k `wmain`.

## <a name="see-also"></a>Viz také

[Globální proměnné](../c-runtime-library/global-variables.md)