---
title: feholdexcept2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: feholdexcept
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
- feholdexcept
- fenv/feholdexcept
dev_langs: C++
helpviewer_keywords: feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfc0ce4da07bb83fbe003e7ea23029628f4e199b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="feholdexcept"></a>feholdexcept
Uloží aktuální prostředí s plovoucí desetinnou čárkou v zadaný objekt, vymaže příznaky s plovoucí desetinnou čárkou stavu a, pokud je to možné, převede s plovoucí desetinnou čárkou prostředí do režimu bez zastavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `penv`  
 Ukazatel na `fenv_t` objekt, který má obsahovat kopii v prostředí s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu nula, pokud funkce se bude moct úspěšně zapnout zpracování výjimek plovoucí desetinné čárky bez zastavení.  
  
## <a name="remarks"></a>Poznámky  
 `feholdexcept` Funkce slouží k uložení stavu aktuální plovoucí bodu prostředí v `fenv_t` objektu na kterou odkazuje `penv`a k nastavení prostředí tak, aby není přerušení spuštění na s plovoucí desetinnou čárkou výjimky. To se označuje jako bez zastavení režimu.  Tento režim pokračuje, dokud prostředí je obnovit pomocí [fesetenv](fesetenv1.md) nebo [feupdateenv](../../c-runtime-library/reference/feupdateenv.md).  
  
 Tuto funkci můžete použít na začátku podprogramu vyžadující skrýt jednu nebo více výjimek plovoucí desetinné čárky volající. Chcete-li sestavu výjimku, jednoduše zrušte nežádoucí výjimky pomocí [feclearexcept,](../../c-runtime-library/reference/feclearexcept1.md) a pak ukončete bez zastavení režimu se volání `feupdateenv`.  
  
 Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h >|\<cfenv >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](fesetenv1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)