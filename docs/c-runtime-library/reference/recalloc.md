---
title: "_recalloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _recalloc
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
- _recalloc
- recalloc
dev_langs: C++
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 007f174b3cbdb7e8ca53af19b6f9764200ff690a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recalloc"></a>_recalloc
Kombinace `realloc` a `calloc`. Přidělí pole v paměti a inicializuje jeho prvky na hodnotu 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_recalloc(   
   void *memblock  
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatel na dříve přidělenou paměť bloku.  
  
 `num`  
 Počet elementů.  
  
 `size`  
 Délka v bajtech jednotlivých prvků.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_recalloc`Vrátí `void` ukazatel na oblast paměti opětovnému přidělení (a případně přesouvat).  
  
 Pokud není k dispozici dostatek paměti k rozšíření na danou velikost bloku, původní blok je vlevo beze změny, a `NULL` je vrácen.  
  
 Pokud požadovaná velikost je nulová, pak bloku na kterou odkazuje `memblock` uvolněno; vrácená hodnota je `NULL`, a `memblock` je ponechán jednotka ukazovat na uvolněné blok.  
  
 Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ jinými než `void`, používat typ, který přetypovat na návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `_recalloc` Funkce se změní velikost bloku přidělené paměti. `memblock` Argument odkazuje na začátku bloku paměti. Pokud `memblock` je `NULL`, `_recalloc` se chová stejně jako [calloc –](../../c-runtime-library/reference/calloc.md) a přiděluje nový blok `num`  *  `size` bajtů. Každý prvek je inicializován na hodnotu 0. Pokud `memblock` není `NULL`, by mělo být ukazatel vrácené z předchozího volání `calloc`, [malloc –](../../c-runtime-library/reference/malloc.md), nebo [realloc –](../../c-runtime-library/reference/realloc.md).  
  
 Vzhledem k nového bloku můžou být nové umístění paměti, ukazatele vrácený `_recalloc` nemusí být předána ukazatele `memblock` argument.  
  
 `_recalloc`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo velikost paměti požadované překračuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `recalloc`volání `realloc` Chcete-li použít C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce nastavit nový režim obslužné rutiny. Nový režim obslužná rutina označuje, jestli při selhání, `realloc` je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md). Ve výchozím nastavení `realloc` nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když `_recalloc` nepodaří přidělit paměť, `realloc` volání nové rutiny obslužná rutina ve stejné způsobem, jako `new` operátor nepodporuje, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí nastavení, volejte  
  
```  
_set_new_mode(1)  
```  
  
 časná v aplikaci nebo odkaz s NEWMODE.OBJ.  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `_recalloc` přeloží na [_recalloc_dbg –](../../c-runtime-library/reference/recalloc-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_recalloc`je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že není k úpravě globálních proměnných, že ukazatele vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_recalloc`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [_recalloc_dbg –](../../c-runtime-library/reference/recalloc-dbg.md)   
 [_aligned_recalloc –](../../c-runtime-library/reference/aligned-recalloc.md)   
 [_aligned_offset_recalloc –](../../c-runtime-library/reference/aligned-offset-recalloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [Možnosti odkazů](../../c-runtime-library/link-options.md)