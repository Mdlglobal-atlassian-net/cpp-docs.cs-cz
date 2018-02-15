---
title: "_aligned_offset_recalloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_offset_recalloc
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
- aligned_offset_recalloc
- _aligned_offset_recalloc
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_recalloc function
- _aligned_offset_recalloc function
ms.assetid: a258f54e-eeb4-4853-96fc-007d710f98e9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84cf4f353d71cd5fc21957dc0ab9178982ad6030
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alignedoffsetrecalloc"></a>_aligned_offset_recalloc
Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_offset_recalloc(  
   void *memblock,   
   size_t num,   
   size_t size,   
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Aktuální ukazatel bloku paměti.  
  
 `num`  
 Počet elementů.  
  
 `size`  
 Délka v bajtech jednotlivých prvků.  
  
 `alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 `offset`  
 Posun do přidělení paměti vynutit zarovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_aligned_offset_recalloc` vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je `NULL` Pokud velikost je nula a argument vyrovnávací paměti není `NULL`, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. V druhém případě je původní blok beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.  
  
 `_aligned_offset_recalloc` je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné a že má ukazatel vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
## <a name="remarks"></a>Poznámky  
 Jako [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_recalloc` umožňuje struktura zarovnána na posun v rámci struktury.  
  
 `_aligned_offset_recalloc` je založena na `malloc`. Další informace o používání `_aligned_offset_malloc`, najdete v části [malloc –](../../c-runtime-library/reference/malloc.md). Pokud `memblock` je `NULL`, volání funkce `_aligned_offset_malloc` interně.  
  
 Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud požadovaná velikost (`num` * `size`) byla větší než `_HEAP_MAXREQ`. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_offset_recalloc` ověří jeho parametry. Pokud `alignment` není mocninou 2 nebo, pokud `offset` je větší než nebo rovna požadované velikosti a nenulové hodnoty, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_offset_recalloc`|\<malloc.h>|  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání dat](../../c-runtime-library/data-alignment.md)   
 [_recalloc](../../c-runtime-library/reference/recalloc.md)   
 [_aligned_recalloc](../../c-runtime-library/reference/aligned-recalloc.md)