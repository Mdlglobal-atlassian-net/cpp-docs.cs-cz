---
title: "_aligned_free – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_free
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
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30b37b6424b02ffb4eab6f1d90d03d7b2a3154b2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alignedfree"></a>_aligned_free
Uvolní blok paměti, který byl přidělen s [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatele na blok paměti, který byl vrácen do `_aligned_malloc` nebo `_aligned_offset_malloc` funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_free` je označena `__declspec(noalias)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).  
  
 Tuto funkci nelze ověřit její parametr, na rozdíl od jiných funkcí CRT _aligned. Pokud `memblock` je `NULL` ukazatele, tato funkce jednoduše provede žádná akce. Změny jsou `errno` a nevyvolá obslužná rutina neplatný parametr. Pokud dojde k chybě ve funkci kvůli pomocí funkcí _aligned není dříve přidělit blok paměti nebo dojde k chybě synchronizace paměti z důvodu některých nepředpokládaného calamity, funkce generuje sestavy ladění z [_RPT, _RPTF, _RPTW, _ Rptfw – makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_free`|\<malloc.h>|  
  
## <a name="example"></a>Příklad  
 Další informace najdete v tématu [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání dat](../../c-runtime-library/data-alignment.md)