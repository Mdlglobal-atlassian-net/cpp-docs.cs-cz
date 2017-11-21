---
title: "_query_new_mode – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _query_new_mode
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
- query_new_mode
- _query_new_mode
dev_langs: C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f5cc42ee9aaeccfacf7088f5cc80a3d305169b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="querynewmode"></a>_query_new_mode
Vrací celočíselnou hodnotu označující nový režim obslužná rutina, která nastavuje `_set_new_mode` pro `malloc`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální novou obslužnou rutinu režim, konkrétně 0 nebo 1, pro `malloc`. Návratová hodnota 1 značí, že při selhání při přidělování paměti, `malloc` volání nové rutiny obslužná rutina; vrácená hodnota 0 značí, že tomu tak není.  
  
## <a name="remarks"></a>Poznámky  
 C++ `_query_new_mode` funkce vrátí celé číslo, které označuje nový režim obslužná rutina, kterou je nastavit C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce pro [malloc –](../../c-runtime-library/reference/malloc.md). Nový režim obslužná rutina označuje, jestli při selhání při přidělování paměti, `malloc` je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md). Ve výchozím nastavení `malloc` nevyvolá nové rutiny ovladače při selhání. Můžete použít `_set_new_mode` toto chování potlačit, která při selhání `malloc` volání nové rutiny obslužná rutina ve stejné způsobem **nové** operátor nepodporuje, když se nepodaří přidělit paměť. Další informace najdete v tématu diskuzi o [nové a odstraňte operátory](../../cpp/new-and-delete-operators.md) v referenční příručka jazyka C++.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_query_new_mode`|\<New.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler –](../../c-runtime-library/reference/query-new-handler.md)