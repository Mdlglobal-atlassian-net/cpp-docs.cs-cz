---
title: ___lc_codepage_func | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
dev_langs: C++
helpviewer_keywords: ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8532984c8557b095753c0e8cf30b6e63d8b01ce0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lccodepagefunc"></a>___lc_codepage_func
Vnitřní funkce CRT. Načte aktuální stránky kód vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Aktuální znaková stránka vlákno.  
  
## <a name="remarks"></a>Poznámky  
 `___lc_codepage_func`je interní funkce CRT, používaný jiných funkcí CRT se získat aktuální znaková stránka z lokální úložiště vláken pro CRT data. Tyto informace jsou k dispozici také pomocí [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md) funkce.  
  
 A *znaková stránka* mapování kódů jednobajtové nebo dvoubajtové jednotlivých znaků. Jiné znakové stránky obsahovat jiné speciální znaky, obvykle přizpůsobené pro jazyk nebo skupina jazyků. Další informace o znakové stránky najdete v tématu [znakové stránky](../c-runtime-library/code-pages.md).  
  
 CRT – vnitřní funkce jsou specifické pro implementaci a mohou podléhat změnám jednotlivých verzí. Nedoporučujeme jejich použití v kódu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`___lc_codepage_func`|crt\src\setlocal.h|  
  
## <a name="see-also"></a>Viz také  
 [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale –, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)