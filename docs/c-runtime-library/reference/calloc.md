---
title: calloc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- calloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6986e1caec25cd544919039f690544af429524af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394883"
---
# <a name="calloc"></a>calloc

Pole v paměti přidělí u elementů na hodnotu 0.

## <a name="syntax"></a>Syntaxe

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Číslo*<br/>
Počet elementů.

*Velikost*<br/>
Délka v bajtech jednotlivých prvků.

## <a name="return-value"></a>Návratová hodnota

**calloc –** vrací ukazatel na přidělené místo. Prostor úložiště ukazuje návratovou hodnotu záruku, že vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ jinými než **void**, používat typ, který přetypovat na návratovou hodnotu.

## <a name="remarks"></a>Poznámky

**Calloc –** funkce přidělí prostor úložiště pro pole *číslo* elementy, každý o délce *velikost* bajtů. Každý prvek je inicializován na hodnotu 0.

**calloc –** nastaví **errno** k **enomem –** Pokud selže přidělení paměti nebo velikost paměti požadované překračuje **_heap_maxreq –**. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc –** volání **malloc –** používat C++ [_set_new_mode –](set-new-mode.md) funkce nastavit nový režim obslužné rutiny. Nový režim obslužná rutina označuje, jestli při selhání, **malloc –** je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](set-new-handler.md). Ve výchozím nastavení **malloc** nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když **calloc –** nepodaří přidělit paměť, **malloc –** volání nové rutiny obslužná rutina ve stejné způsobem **nové** nemá operátor Když dojde k chybě ze stejného důvodu. Chcete-li přepsat výchozí nastavení, volejte

```C
_set_new_mode(1);
```

časná v aplikaci nebo odkaz s NEWMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).

Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, **calloc –** přeloží na [_calloc_dbg –](calloc-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc –** je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že není k úpravě globálních proměnných, že ukazatele vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**calloc**|\<stdlib.h > a \<malloc.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
