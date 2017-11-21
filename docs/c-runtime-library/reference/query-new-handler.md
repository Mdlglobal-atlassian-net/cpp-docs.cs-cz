---
title: "_query_new_handler – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _query_new_handler
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
- _query_new_handler
- query_new_handler
dev_langs: C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b245286294a74718b7527728d5d9e8dea9793234
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="querynewhandler"></a>_query_new_handler
Vrátí adresu aktuální nové rutiny obslužná rutina.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_PNH _query_new_handler(  
   void   
);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu aktuální nové rutiny obslužných rutin jako sady podle `_set_new_handler`.  
  
## <a name="remarks"></a>Poznámky  
 C++ `_query_new_handler` funkce vrátí adresu aktuální zpracování výjimek funkce, která nastavuje C++ [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md) funkce. `_set_new_handler`slouží k určení funkce zpracování výjimek, které má získat kontrolu, pokud **nové** operátor se nepodařilo přidělit paměť. Další informace najdete v tématu diskuzi o [nové a odstraňte operátory](../../cpp/new-and-delete-operators.md) v referenční příručka jazyka C++.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_query_new_handler`|\<New.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)