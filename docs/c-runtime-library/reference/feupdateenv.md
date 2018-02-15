---
title: feupdateenv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- feupdateenv
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd4a74515b2b3ab29b30fb07d80121e35d950ee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="feupdateenv"></a>feupdateenv
Uloží aktuálně vyvolané výjimky s plovoucí desetinnou čárkou, obnoví stav zadaného prostředí s plovoucí desetinnou čárkou a poté vyvolá uložené výjimky s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `penv`  
 Ukazatel na `fenv_t` objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Použití makra FE_DFL_ENV, můžete také zadat výchozí spouštěcí prostředí s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud se všechny akce úspěšně dokončit. Jinak vrátí nenulovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `feupdateenv` Funkce provádí různé akce. Nejprve ukládá aktuální stav příznaky výjimky vyvolané s plovoucí desetinnou čárkou v automatické úložiště. Potom nastaví z s hodnotou uloženou v aktuálním prostředí s plovoucí desetinnou čárkou `fenv_t` objektu na kterou odkazuje `penv`. Pokud `penv` není FE_DFL_ENV nebo neodkazuje na platný `fenv_t` objektu následné chování není definován. Nakonec `feupdateenv` vyvolá místně uložené výjimky s plovoucí desetinnou čárkou.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`feupdateenv`|\<fenv.h>|\<cfenv>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)