---
title: fesetenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs: C++
helpviewer_keywords: fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64e630afb575523abcb790c29dcd198ba34f263b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fesetenv"></a>fesetenv
Nastaví aktuální prostředí s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `penv`  
 Ukazatel na `fenv_t` objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Použití makra FE_DFL_ENV, můžete také zadat výchozí spouštěcí prostředí s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud prostředí byl úspěšně nastaven. Jinak vrátí nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `fesetenv` Funkce nastaví z s hodnotou uloženou v aktuálním prostředí s plovoucí desetinnou čárkou `fenv_t` objektu na kterou odkazuje `penv`. Procedura bodu prostředí je sada příznaky stavu a řízení režimy, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje zaokrouhlení režimu a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud `penv` není FE_DFL_ENV nebo neodkazuje na platný `fenv_t` objektu následné chování není definován.  
  
 Volání této funkce nastaví výjimku příznaky stavu, které jsou v `penv` objektu, ale nevyvolá tyto výjimky.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fesetenv`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)