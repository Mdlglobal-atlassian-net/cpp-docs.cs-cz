---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: b510d16b6e784202094bb05e6364f7af1b1fff97
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939921"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

Uvolňuje blok paměti, který byl přidělen pomocí [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md) (pouze ladění).

## <a name="syntax"></a>Syntaxe

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Ukazatel na blok paměti, který byl vrácen do funkce [_aligned_malloc](aligned-malloc.md) nebo [_aligned_offset_malloc](aligned-offset-malloc.md) .

## <a name="remarks"></a>Poznámky

Funkce **_aligned_free_dbg** je ladicí verze funkce [_aligned_free](aligned-free.md) . Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_aligned_free_dbg** je sníženo na volání `_aligned_free`. I `_aligned_free` **_aligned_free_dbg** uvolňují blok paměti v základní haldě, ale **_aligned_free_dbg** je součástí ladění: schopnost uchovávat uvolněné bloky v propojeném seznamu haldy, aby simulovaly nedostatečné paměťové podmínky.

**_aligned_free_dbg** provádí kontrolu platnosti všech zadaných souborů a zablokuje jejich umístění před provedením bezplatné operace. Neočekává se, že aplikace tyto informace poskytne. Když je blok paměti uvolněn, Správce haldy ladění automaticky zkontroluje integritu vyrovnávací paměti na obou stranách uživatelské části a vydá zprávu o chybě, pokud došlo k přepsání. Pokud je nastavené bitové pole _CRTDBG_DELAY_FREE_MEM_DF s příznakem [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , je uvolněný blok vyplněn hodnotou 0xDD, přiřazený typ bloku _FREE_BLOCK a zůstane v propojeném seznamu bloků paměti haldy.

Pokud při uvolnění paměti dojde k chybě, `errno` je nastavena s informacemi z operačního systému podle povahy selhání. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)