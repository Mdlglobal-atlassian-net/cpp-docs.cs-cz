---
title: _free_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_dbg
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
- _free_dbg
- free_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa485eea6f0ffda05b0ef33a808d5ec837255514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="freedbg"></a>_free_dbg

Uvolní blok paměti haldy (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parametry

*userData* ukazatel na oblast paměti přidělené na uvolnění.

*blockType* typ bloku přidělenou paměť na uvolnění: **_client_block –**, **_normal_block –**, nebo **_ignore_block –**.

## <a name="remarks"></a>Poznámky

**_Free_dbg –** funkce je ladicí verze [volné](free.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání **_free_dbg –** byla snížena volání **volné**. Obě **volné** a **_free_dbg –** volné paměti blok v haldě základní ale **_free_dbg –** může vyrovnávat dvě funkce ladění: schopnost zachovat uvolněné bloků v do haldy odkazovaného seznamu k simulaci nedostatek paměti a parametr typ bloku k bezplatným přidělení konkrétní typy.

**_free_dbg –** provede kontrolu platnosti na všechny zadané soubory a umístění bloku před provedením operace volné. Aplikace není očekáván poskytnout tyto informace. Když po uvolnění paměti blok správce haldy ladění automaticky ověří integritu vyrovnávací paměti na obou stranách části uživatele a vydá zprávu o chybách v případě, že došlo k přepsání. Pokud **_crtdbg_delay_free_mem_df –** bitová pole [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) je příznak nastaven, uvolněné blok je vyplněn přiřazenou hodnotu 0xDD, **_free_block –** blokovat typ, a zachovány v haldě na odkazovaného seznamu bloků paměti.

Pokud dojde k chybě v uvolnění paměti, **errno** je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad, jak pomocí **_free_dbg –**, najdete v části [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
