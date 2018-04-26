---
title: _aligned_free_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efbe33940a4dad3ddb3ce73809ae2dc31f6d05c6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Uvolní blok paměti, který byl přidělen s [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) (pouze ladění).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock* ukazatele na blok paměti, který byl vrácen do [_aligned_malloc –](aligned-malloc.md) nebo [_aligned_offset_malloc –](aligned-offset-malloc.md) funkce.

## <a name="remarks"></a>Poznámky

**_Aligned_free_dbg –** funkce je ladicí verze [_aligned_free –](aligned-free.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_aligned_free_dbg –** byla snížena volání **_aligned_free –**. Obě **_aligned_free –** a **_aligned_free_dbg –** volné paměti blok základní haldy, ale **_aligned_free_dbg –** může vyrovnávat funkce ladění: schopnost zachovat uvolněné bloky v haldě na odkazovaného seznamu k simulaci nedostatek paměti.

**_aligned_free_dbg –** provede kontrolu platnosti na všechny zadané soubory a umístění bloku před provedením operace volné. Aplikace není očekáván poskytnout tyto informace. Když po uvolnění paměti blok správce haldy ladění automaticky ověří integritu vyrovnávací paměti na obou stranách části uživatele a vydá zprávu o chybách v případě, že došlo k přepsání. Pokud **_crtdbg_delay_free_mem_df –** bitová pole [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) je příznak nastaven, uvolněné blok je vyplněn přiřazenou hodnotu 0xDD, **_free_block –** blokovat typ, a zachovány v haldě na odkazovaného seznamu bloků paměti.

Pokud dojde k chybě v uvolnění paměti, **errno** je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
