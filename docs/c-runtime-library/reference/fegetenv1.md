---
title: fegetenv1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetegenv
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetenv
- fenv/fegetenv
dev_langs: C++
helpviewer_keywords: fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d4dd358f8fe2d3fff374535f5ef4eb892aa1a125
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fegetenv"></a>fegetenv
Uloží aktuální prostředí s plovoucí desetinnou čárkou v zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `penv`  
 Ukazatel na `fenv_t` objektu tak, aby obsahovala aktuální hodnoty s plovoucí desetinnou čárkou prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud je s plovoucí desetinnou čárkou prostředí byl úspěšně uložen v `penv`. Jinak vrátí hodnotu nula.  
  
## <a name="remarks"></a>Poznámky  
 `fegetenv` Funkce uloží aktuální prostředí s plovoucí desetinnou čárkou v objektu, na kterou odkazuje `penv`. Procedura bodu prostředí je sada příznaky stavu a řízení režimy, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje režim směr zaokrouhlení a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud `penv` neodkazuje na platný `fenv_t` objektu následné chování není definován.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fegetenv`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)