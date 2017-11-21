---
title: "_aligned_free_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_free_dbg
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
dev_langs: C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 724acaed1c99aa2507c33010e97f3f993e1b6de6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg
Uvolní blok paměti, který byl přidělen s [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladění).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _aligned_free_dbg(  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatele na blok paměti, který byl vrácen do `_aligned_malloc` nebo `_aligned_offset_malloc` funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_free_dbg` Funkce je ladicí verze [_aligned_free –](../../c-runtime-library/reference/aligned-free.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_aligned_free_dbg` byla snížena volání `_aligned_free`. Obě `_aligned_free` a `_aligned_free_dbg` volné paměti blok základní haldy, ale `_aligned_free_dbg` může vyrovnávat funkce ladění: schopnost zachovat uvolněné bloků v haldě na odkazovaného seznamu k simulaci nedostatek paměti.  
  
 `_aligned_free_dbg`provede kontrolu platnosti na všechny zadané soubory a umístění bloku před provedením operace volné. Aplikace není očekáván poskytnout tyto informace. Když po uvolnění paměti blok správce haldy ladění automaticky ověří integritu vyrovnávací paměti na obou stranách části uživatele a vydá zprávu o chybách v případě, že došlo k přepsání. Pokud `_CRTDBG_DELAY_FREE_MEM_DF` bitová pole [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) je příznak nastaven, uvolněné blok je vyplněn přiřazenou hodnotu 0xDD, `_FREE_BLOCK` blokovat typ a uchovává se v haldě na odkazovaného seznamu bloků paměti.  
  
 Pokud dojde k chybě v uvolnění paměti, `errno` je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_free_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)