---
title: atexit
ms.date: 11/04/2016
apiname:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 48f0fbfa1f3350f73899fcdbb3bf7922f1c6174d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341584"
---
# <a name="atexit"></a>atexit

Zpracuje zadané funkce při ukončení.

## <a name="syntax"></a>Syntaxe

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parametry

*Func*<br/>
Funkce, která se má volat.

## <a name="return-value"></a>Návratová hodnota

**AtExit** vrátí 0 v případě úspěchu nebo nenulovou hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Atexit** funkce je předána adresu funkce *func* se volá, když program ukončen normálně. Následná volání **atexit** vytvořit registr funkcí, které jsou spouštěny popořadě poslední dovnitř, první (ven LIFO). Funkce předány **atexit** nemůže mít parametry. **AtExit** a **_onexit** použití haldy pro uložení do registru funkce. Díky tomu se počet funkcí, které mohou být registrovány je omezen pouze haldy paměti.

Kód v **atexit** funkce by neměla obsahovat závislost na žádné knihovny DLL, které by mohly mít již uvolněna při **atexit** funkce je volána.

Chcete-li generovat aplikace vyhovující standardu ANSI, použijte standardu ANSI **atexit** – funkce (místo podobný **_onexit** funkce).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Příklad

Tento program nabízených oznámení v ceně čtyři funkce do zásobníku funkce, který se spustí při **atexit** je volána. Při ukončení programu tyto programy se provádějí v poslední dovnitř, první na základě.

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
