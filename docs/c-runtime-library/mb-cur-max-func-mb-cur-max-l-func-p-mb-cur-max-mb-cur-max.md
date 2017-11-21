---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
dev_langs: C++
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c071ddafad89dc284aebea2dc49d74385feb91da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
Vnitřní funkce CRT. Načte maximální počet bajtů v vícebajtových znaků pro zadané nebo aktuální národní prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int ___mb_cur_max_func(void);  
int ___mb_cur_max_l_func(_locale_t locale);  
int * __p___mb_cur_max(void);  
#define __mb_cur_max (___mb_cur_max_func())  
```  
  
#### <a name="parameters"></a>Parametry  
 locale  
 Struktura národního prostředí načíst výsledky z. Pokud má hodnotu null, použije se aktuální národní prostředí vlákna.  
  
## <a name="return-value"></a>Návratová hodnota  
 Maximální počet bajtů v vícebajtových znaků pro aktuální národní prostředí vlákna nebo zadaný národní prostředí.  
  
## <a name="remarks"></a>Poznámky  
 Toto je interní funkce, která CRT používá k načtení aktuální hodnota [mb_cur_max –](../c-runtime-library/mb-cur-max.md) makro z lokální úložiště vláken. Doporučujeme vám, že používáte `MB_CUR_MAX` makro ve vašem kódu pro přenositelnost.  
  
 `__mb_cur_max` Makro je pohodlný způsob, jak `___mb_cur_max_func()` funkce. `__p___mb_cur_max` Je definována funkce pro kompatibilitu s Visual C++ 5.0 a starší verze.  
  
 CRT – vnitřní funkce jsou specifické pro implementaci a mohou podléhat změnám jednotlivých verzí. Nedoporučujeme jejich použití v kódu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h >, \<stdlib.h >|  
  
## <a name="see-also"></a>Viz také  
 [MB_CUR_MAX –](../c-runtime-library/mb-cur-max.md)