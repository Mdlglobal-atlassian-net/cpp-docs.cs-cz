---
title: ___lc_collate_cp_func | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ___lc_collate_cp_func
apilocation:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords: ___lc_collate_cp_func
dev_langs: C++
helpviewer_keywords: ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe7ff6ce073f84a87e2243ab98d3b99af0dfd22c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lccollatecpfunc"></a>___lc_collate_cp_func
Vnitřní funkce CRT. Načte aktuální stránky kód kolace vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Aktuální stránky kód kolace vlákno.  
  
## <a name="remarks"></a>Poznámky  
 `___lc_collate_cp_func`je interní funkce CRT, používaný jiných funkcí CRT se získat aktuální znaková stránka kolace z lokální úložiště vláken pro CRT data. Tyto informace jsou k dispozici také pomocí [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md) funkce.  
  
 CRT – vnitřní funkce jsou specifické pro implementaci a mohou podléhat změnám jednotlivých verzí. Nedoporučujeme jejich použití v kódu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`___lc_collate_cp_func`|crt\src\setlocal.h|  
  
## <a name="see-also"></a>Viz také  
 [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale –, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)