---
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: b91e6dad81f006b0b94ac17a940e840386f6d2b1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939663"
---
# <a name="atexit"></a>atexit

Zpracuje zadanou funkci při ukončení.

## <a name="syntax"></a>Syntaxe

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>Parametry

*func*<br/>
Funkce, která má být volána.

## <a name="return-value"></a>Návratová hodnota

**atexit** vrátí 0 v případě úspěchu nebo nenulovou hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **atexit** je předána adresou funkce *Func* funkce, která se má volat při normálním ukončení programu. Po sobě jdoucí volání **atexit** vytvořit registr funkcí, které jsou spouštěny v pořadí poslední v, první ven (LIFO). Funkce předané do **atexit** nemohou přijímat parametry. **atexit** a **_onexit** používají haldu k uložení registru funkcí. Počet funkcí, které lze registrovat, je tedy omezen pouze pamětí haldy.

Kód ve funkci **atexit** by neměl obsahovat žádnou závislost na žádné knihovně DLL, která by již byla uvolněna při volání funkce **atexit** .

K vygenerování aplikace kompatibilní se standardem ANSI použijte funkci **atexit** standardu ANSI (místo podobné funkce **_onexit** ).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>Příklad

Tento program vloží čtyři funkce do zásobníku funkcí, které mají být provedeny při volání funkce **atexit** . Když se program ukončí, tyto programy se spustí na začátku a prvním základě.

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
