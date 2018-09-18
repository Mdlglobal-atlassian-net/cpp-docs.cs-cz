---
title: _aligned_free_dbg – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae9adaf1037297dfae9ba78f6f872544a5555ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081673"
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Uvolní blok paměti, která byla přidělena pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) (pouze debug).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatele na blok paměti, která se vrátila [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_Aligned_free_dbg –** ladicí verzi je funkce [_aligned_free –](aligned-free.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_free_dbg –** je omezená na volání `_aligned_free`. Obě `_aligned_free` a **_aligned_free_dbg –** uvolnění bloku paměti v haldě základní, ale **_aligned_free_dbg –** obsáhne funkce ladění: možnost zachovat uvolněné bloky v propojeném seznamu haldy pro simulujte podmínky nedostatku paměti.

**_aligned_free_dbg –** provede kontrolu platnosti na všechny zadané soubory a umístění bloku před provedením operace zdarma. Tyto informace poskytnout neočekává se aplikace. Při uvolnění bloku paměti správce hald ladění automaticky kontroluje integritu vyrovnávací paměti na obou stranách část uživatele a vydá zprávu o chybě, pokud došlo k přepsání. Pokud _CRTDBG_DELAY_FREE_MEM_DF bitová pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) je příznak nastaven, vyplněny 0xDD hodnotu, přiřadit typ bloku _FREE_BLOCK a uchovávány v propojeném seznamu haldy bloků paměti uvolněné bloku.

Pokud dojde k chybě v uvolňování paměti, `errno` nastaven s informacemi z operačního systému na povaze selhání. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)