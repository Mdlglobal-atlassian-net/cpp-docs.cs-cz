---
title: "Kontrola chyb za běhu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.runtime
dev_langs: C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc3f87c5841ce99219ba0d5bac55e70852df632d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="run-time-error-checking"></a>Kontrola chyb za běhu
Běhové knihovny jazyka C obsahuje funkce, které podporují Kontrola chyb za běhu (RTC). Kontrola chyb za běhu umožňuje sestavením programu tak, že se hlásí určité druhy běhové chyby. Určete způsob hlášení chyb a jaké druhy chyb jsou hlášeny. Další informace najdete v tématu [postupy: použití nativního Run-Time kontroluje](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
 Chcete-li přizpůsobit způsob, jakým vašeho programu nemá Kontrola chyb za běhu použijte následující funkce.  
  
### <a name="run-time-error-checking-functions"></a>Chyba při spuštění kontroly funkce  
  
|Funkce|Použití|  
|--------------|---------|  
|[_Rtc_geterrdesc –](../c-runtime-library/reference/rtc-geterrdesc.md)|Vrátí stručný popis typu Chyba spuštění kontroly.|  
|[_Rtc_numerrors –](../c-runtime-library/reference/rtc-numerrors.md)|Vrátí celkový počet chyb, které lze vyhledat podle Kontrola chyb za běhu.|  
|[_Rtc_seterrorfunc –](../c-runtime-library/reference/rtc-seterrorfunc.md)|Funkce označí jako obslužná rutina pro vytváření sestav Kontrola chyb za běhu.|  
|[_Rtc_seterrortype –](../c-runtime-library/reference/rtc-seterrortype.md)|Přidruží k chybě, která se zjišťují pomocí Kontrola chyb za běhu s typem.|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [/ RTC (Kontrola chyb za běhu)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime_checks –](../preprocessor/runtime-checks.md)   
 [Rutiny ladění](../c-runtime-library/debug-routines.md)