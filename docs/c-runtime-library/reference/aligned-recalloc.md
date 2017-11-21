---
title: "_aligned_recalloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
dev_langs: C++
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6fb5a95cab9942c36f9578315e73392984435059
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignedrecalloc"></a>_aligned_recalloc
Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md) a inicializuje paměť na 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_recalloc(  
   void *memblock,   
   size_t num,  
   size_t size,   
   size_t alignment  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`memblock`  
 Aktuální ukazatel bloku paměti.  
  
 [v]`num`  
 Počet elementů.  
  
 [v]`size`  
 Velikost v bajtech jednotlivých prvků.  
  
 [v]`alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_aligned_recalloc`vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je `NULL` Pokud velikost je nula a argument vyrovnávací paměti není `NULL`, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. V druhém případě je původní blok beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.  
  
 Jedná se o chybu, znovu přidělte paměť a změňte zarovnání bloku.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_recalloc`je založena na `malloc`. Další informace o používání `_aligned_offset_malloc`, najdete v části [malloc –](../../c-runtime-library/reference/malloc.md).  
  
 Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost `_HEAP_MAXREQ`. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_recalloc` ověří jeho parametry. Pokud `alignment` není napájení 2, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_recalloc`|\<malloc.h >|  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání dat](../../c-runtime-library/data-alignment.md)   
 [_recalloc –](../../c-runtime-library/reference/recalloc.md)   
 [_aligned_offset_recalloc –](../../c-runtime-library/reference/aligned-offset-recalloc.md)