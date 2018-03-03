---
title: "Kontrola chyb za běhu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 981e8c04b305ccef12a463b0a4defd3017916b82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="run-time-error-checking"></a>Kontrola chyb za běhu
Běhové knihovny jazyka C obsahuje funkce, které podporují Kontrola chyb za běhu (RTC). Kontrola chyb za běhu umožňuje sestavením programu tak, že se hlásí určité druhy běhové chyby. Určete způsob hlášení chyb a jaké druhy chyb jsou hlášeny. Další informace najdete v tématu [postupy: použití nativního Run-Time kontroluje](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Chcete-li přizpůsobit způsob, jakým vašeho programu nemá Kontrola chyb za běhu použijte následující funkce.  
  
### <a name="run-time-error-checking-functions"></a>Chyba při spuštění kontroly funkce  
  
|Funkce|Použití|  
|--------------|---------|  
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Vrátí stručný popis typu Chyba spuštění kontroly.|  
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Vrátí celkový počet chyb, které lze vyhledat podle Kontrola chyb za běhu.|  
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Funkce označí jako obslužná rutina pro vytváření sestav Kontrola chyb za běhu.|  
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Přidruží k chybě, která se zjišťují pomocí Kontrola chyb za běhu s typem.|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [/ RTC (Kontrola chyb za běhu)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime_checks –](../preprocessor/runtime-checks.md)   
 [Rutiny ladění](../c-runtime-library/debug-routines.md)