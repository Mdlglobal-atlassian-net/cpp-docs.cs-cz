---
title: _free_dbg
ms.date: 11/04/2016
api_name:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 43591ce8710dd25ad33832a5f084ca6e84bba979
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956805"
---
# <a name="_free_dbg"></a>_free_dbg

Uvolňuje blok paměti v haldě (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na přidělený blok paměti, který se má uvolnit.

*blockType*<br/>
Typ přiděleného bloku paměti, který se má uvolnit: **_CLIENT_BLOCK**, **_NORMAL_BLOCK**nebo **_IGNORE_BLOCK**.

## <a name="remarks"></a>Poznámky

Funkce **_free_dbg** je ladicí verze [bezplatné](free.md) funkce. Pokud není definován [_DEBUG](../../c-runtime-library/debug.md) , každé volání **_free_dbg** je sníženo na **bezplatné**volání. **Bezplatný** i **_free_dbg** uvolňuje blok paměti v základní haldě, ale **_free_dbg** poskytuje dvě funkce ladění: schopnost uchovávat uvolněné bloky v propojeném seznamu haldy, aby simulovaly nedostatečné paměťové podmínky a parametr typu bloku pro bezplatné konkrétní typy přidělení.

**_free_dbg** provádí kontrolu platnosti všech zadaných souborů a zablokuje jejich umístění před provedením bezplatné operace. Neočekává se, že aplikace tyto informace poskytne. Když je blok paměti uvolněn, Správce haldy ladění automaticky zkontroluje integritu vyrovnávací paměti na obou stranách uživatelské části a vydá zprávu o chybě, pokud došlo k přepsání. Pokud je nastavené bitové pole **_CRTDBG_DELAY_FREE_MEM_DF** s příznakem [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , je uvolněný blok vyplněn hodnotou 0xDD, přiřazený typ bloku **_FREE_BLOCK** a zůstane v propojeném seznamu bloků paměti haldy.

Pokud dojde k chybě při uvolnění paměti, **errno** se nastaví s informacemi z operačního systému podle povahy selhání. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloků přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi voláním standardní funkce haldy a její ladicí verzí v sestavení ladění aplikace najdete v tématu [ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku použití **_free_dbg**naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
