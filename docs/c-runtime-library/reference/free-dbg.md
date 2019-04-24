---
title: _free_dbg
ms.date: 11/04/2016
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
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 5a0024101e4f5a74f1573b271d444b27738db8e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287860"
---
# <a name="freedbg"></a>_free_dbg

Uvolní blok paměti v haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatele na blok paměti přidělené k uvolnění.

*blockType*<br/>
Typ bloku paměti přidělené k uvolnění: **_CLIENT_BLOCK**, **_NORMAL_BLOCK**, nebo **_IGNORE_BLOCK**.

## <a name="remarks"></a>Poznámky

**_Free_dbg –** ladicí verzi je funkce [bezplatné](free.md) funkce. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, každé volání **_free_dbg –** je omezená na volání **bezplatné**. Obě **bezplatné** a **_free_dbg –** uvolnění bloku paměti v haldě základní, ale **_free_dbg –** obsáhne dvou funkcí ladění: možnost zachovat uvolněné bloky v haldy odkazovaného seznamu Simulovat podmínky nedostatku paměti a parametr typu blok k bezplatným alokační typy.

**_free_dbg –** provede kontrolu platnosti na všechny zadané soubory a umístění bloku před provedením operace zdarma. Tyto informace poskytnout neočekává se aplikace. Při uvolnění bloku paměti správce hald ladění automaticky kontroluje integritu vyrovnávací paměti na obou stranách část uživatele a vydá zprávu o chybě, pokud došlo k přepsání. Pokud **_CRTDBG_DELAY_FREE_MEM_DF** bitové pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) je příznak nastaven, uvolněné bloku je vyplněna přiřazenou hodnotu 0xDD, **_FREE_BLOCK** blokovat typu, a uchovávány v propojeném seznamu haldy paměťových bloků.

Pokud dojde k chybě v uvolňování paměti, **errno** nastaven s informacemi z operačního systému na povaze selhání. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsob jejich použití naleznete v tématu [typy bloků na haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce haldy standardní a jeho ladicí verze v sestavení pro ladění aplikace najdete v tématu [ladění verze z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_free_dbg –**, naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
