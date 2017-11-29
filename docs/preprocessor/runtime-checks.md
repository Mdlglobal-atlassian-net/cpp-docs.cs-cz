---
title: "runtime_checks – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs: C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee68bfc7ddace32432f64d4325d9a4c669e0819b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="runtimechecks"></a>runtime_checks
Zakáže nebo obnoví [/RTC](../build/reference/rtc-run-time-error-checks.md) nastavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>Poznámky  
 Nelze povolit spuštění zkontrolujte, zda nebyl povolen s možností kompilátoru. Například pokud nezadáte /RTCs, zadání `#pragma runtime_checks( "s", restore)` neumožní ověřování rámců zásobníku.  
  
 **Runtime_checks –** – Direktiva pragma musí být uvedena mimo funkci a na první funkci definovanou po je vidět – Direktiva pragma se projeví. **Obnovení** a **vypnout** argumenty zapnout zadaný v možnosti *runtime_checks –* zapnout nebo vypnout.  
  
 *Runtime_checks –* může být nula nebo více parametrů uvedené v následující tabulce.  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>Parametry runtime_checks – direktiva Pragma  
  
|Parametry.|Typ kontroly runtime|  
|--------------------|-----------------------------|  
|**s**|Umožňuje zásobníku ověření (snímek).|  
|**c**|Sestavy, když je hodnota přiřazeny menší datový typ, který vede ke ztrátě dat.|  
|**u**|Sestavy při použití proměnné dříve, než je definován.|  
  
 Jedná se o stejná písmena použít s možností/RTC kompilátoru. Příklad:  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 Pomocí **runtime_checks –** – Direktiva pragma s prázdný řetězec (**""**) je speciální forma direktivu:  
  
-   Při použití **vypnout** parametr, stane se kontrola chyb za běhu, uvedené v tabulce výše, vypnutí.  
  
-   Při použití **obnovení** parametr resetuje Kontrola chyb za běhu na ty, které jste zadali s parametrem/RTC kompilátoru.  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   