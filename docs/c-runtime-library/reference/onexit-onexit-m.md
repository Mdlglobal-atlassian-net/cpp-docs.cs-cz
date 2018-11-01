---
title: _onexit, _onexit_m
ms.date: 11/04/2016
apiname:
- _onexit
- _onexit_m
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
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: c190f777032904802f771bab9fc323ba305ff32e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609599"
---
# <a name="onexit-onexitm"></a>_onexit, _onexit_m

Registruje rutiny volat na čas ukončení.

## <a name="syntax"></a>Syntaxe

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>Parametry

*– funkce*<br/>
Ukazatel na funkci, která se má volat při ukončení.

## <a name="return-value"></a>Návratová hodnota

**_onexit** vrací ukazatel na funkci v případě úspěchu nebo **NULL** Pokud není místo k uložení ukazatel na funkci.

## <a name="remarks"></a>Poznámky

**_Onexit** funkce je předána adresu funkce (*funkce*) se volá, když program ukončen normálně. Následná volání **_onexit** vytvořit registr funkcí, které jsou provedeny v pořadí LIFO (last-in-first-out). Funkce předány **_onexit** nemůže mít parametry.

V případě při **_onexit** je volána v rámci knihovny DLL, rutiny zaregistrovaného **_onexit** spustit na knihovnu DLL je po uvolnění **zpracování funkce DllMain** volána s DLL_PROCESS_DETACH.

**_onexit** je rozšířením společnosti Microsoft. Přenositelnost ANSI, použijte [atexit](atexit.md). **_Onexit_m** verze funkce je pro použití ve smíšeném režimu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>Výstup

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
