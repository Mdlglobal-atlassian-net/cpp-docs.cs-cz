---
title: "_aligned_offset_malloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_malloc
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
- _aligned_offset_malloc
- aligned_offset_malloc
dev_langs: C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7322f5a3fbf7bf3d9352181a68db17fad4bc9fcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc
Přidělí paměť na hranici zadané zarovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`size`  
 Velikost velikost paměti požadované přidělení.  
  
 [v]`alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 [v]`offset`  
 Posun do přidělení paměti vynutit zarovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatele na blok paměti, který byl přidělen nebo `NULL` Pokud operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_offset_malloc`je užitečné v situacích, kde je potřeba zarovnání vnořený elementu; například na vnořené třídy se potřeby zarovnání.  
  
 `_aligned_offset_malloc`je založena na `malloc`; Další informace najdete v tématu [malloc –](../../c-runtime-library/reference/malloc.md).  
  
 `_aligned_offset_malloc`je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné a že má ukazatel vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
 Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost `_HEAP_MAXREQ`. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_offset_malloc` ověří jeho parametry. Pokud `alignment` není mocninou 2 nebo, pokud `offset` je větší než nebo rovno `size` a nenulové hodnoty, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_offset_malloc`|\<malloc.h >|  
  
## <a name="example"></a>Příklad  
 Další informace najdete v tématu [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání dat](../../c-runtime-library/data-alignment.md)