---
title: _onexit, _onexit_m
ms.date: 11/04/2016
api_name:
- _onexit
- _onexit_m
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
ms.openlocfilehash: 9afcd729f19f11b82e8f24c2b7fcf9ec40990deb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951347"
---
# <a name="_onexit-_onexit_m"></a>_onexit, _onexit_m

Registruje rutinu, která bude volána v době ukončení.

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

*slouží*<br/>
Ukazatel na funkci, která má být volána při ukončení.

## <a name="return-value"></a>Návratová hodnota

**_onexit** vrací ukazatel na funkci, pokud je úspěch nebo **null** , pokud není k dispozici žádné místo pro uložení ukazatele na funkci.

## <a name="remarks"></a>Poznámky

Funkce **_onexit** je předána adresou funkce (*Function*), která se má volat při normálním ukončení programu. Po sobě jdoucí volání **_onexit** vytvořit registr funkcí, které jsou spuštěny v pořadí LIFO (poslední-in-first-out). Funkce předané do **_onexit** nemohou přijímat parametry.

V případě volání **_onexit** z knihovny DLL jsou rutiny zaregistrované v **_onexit** spuštěny na uvolňování knihovny DLL po volání **DllMain** pomocí DLL_PROCESS_DETACH.

**_onexit** je rozšíření společnosti Microsoft. V případě přenositelnosti ANSI použijte [atexit](atexit.md). Verze **_onexit_m** funkce je určena pro použití ve smíšeném režimu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
