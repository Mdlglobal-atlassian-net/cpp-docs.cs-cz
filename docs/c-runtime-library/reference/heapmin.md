---
title: _heapmin
ms.date: 11/04/2016
apiname:
- _heapmin
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
- _heapmin
- heapmin
helpviewer_keywords:
- heap memory
- minimizing heaps
- memory, releasing
- heaps, releasing unused memory
- _heapmin function
- heapmin function
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
ms.openlocfilehash: 130986894d1e2a68415e6ab9218641eff484ffd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157221"
---
# <a name="heapmin"></a>_heapmin

Uvolní paměť nevyužité haldy v operačním systému.

## <a name="syntax"></a>Syntaxe

```C
int _heapmin( void );
```

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **_heapmin –** vrátí hodnotu 0; v opačném případě vrátí funkce hodnotu -1 a nastaví **errno** k **ENOSYS**.

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Heapmin –** funkce minimalizuje haldy uvolněním nevyužité haldy paměti pro operační systém. Pokud operační systém nepodporuje **_heapmin –**(například Windows 98), vrátí funkce hodnotu -1 a nastaví **errno** k **ENOSYS**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_heapmin**|\<malloc.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapchk](heapchk.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
[malloc](malloc.md)<br/>
