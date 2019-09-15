---
title: _CrtGetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtGetAllocHook
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
- CrtGetAllocHook
- _CrtGetAllocHook
helpviewer_keywords:
- _CrtGetAllocHook function
- CrtGetAllocHook function
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
ms.openlocfilehash: 769621e92bf5f99f76f71b368a3b9a5cd0f79fd0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942407"
---
# <a name="_crtgetallochook"></a>_CrtGetAllocHook

Načte aktuální uživatelsky definovanou funkci přidělení pro zapojování do procesu přidělování paměti ladění C za běhu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuálně definovanou funkci zavěšení přidělení.

## <a name="remarks"></a>Poznámky

**_CrtGetAllocHook** načte aktuální funkci zavěšení aplikace definovanou klientem pro proces přidělení paměti běhové knihovny C run-time.

Další informace o používání dalších funkcí běhu s podporou zavěšení a psaní vlastních funkcí zavěšení definovaných klientem naleznete v tématu [ladění funkce vidlice](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtGetAllocHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetAllocHook](crtsetallochook.md)<br/>
