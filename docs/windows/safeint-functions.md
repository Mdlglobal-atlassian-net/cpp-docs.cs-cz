---
title: Funkce jazyka SafeInt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
caps.latest.revision: "13"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ae482b7f58d64a46b82b32c6c6d62d7f69f0dce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="safeint-functions"></a>Funkce jazyka SafeInt
Knihovna SafeInt nabízí několik funkcí, které můžete použít bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md). Pokud chcete chránit jedné matematické operace z přetečení celé číslo, můžete tyto funkce. Pokud chcete chránit více matematické operace, měli byste vytvořit `SafeInt` objekty. Chcete-li vytvořit je efektivnější `SafeInt` objekty než pomocí těchto funkcí vícekrát.  
  
 Tyto funkce umožňují porovnat nebo provádět matematické operace dva různé typy parametrů bez nutnosti nejprve převést do stejného typu.  
  
 Každá z těchto funkcí má dva typy šablony: `T` a `U`. Každý z těchto typů může být logická hodnota, znak nebo integrální typu. Celočíselné typy můžete podepsané nebo nepodepsané a jakékoli velikosti z 8 bitů na 64 bitů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Sečte dvě čísla a chrání před přetečení.|  
|[SafeCast](../windows/safecast.md)|Vrhá jeden typ parametru k jinému typu.|  
|[SafeDivide](../windows/safedivide.md)|Provede podíl dvou čísel a chrání před dělení nulou.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [SafeNotEquals](../windows/safenotequals.md)|Porovná dvě čísla. Tyto funkce umožňují porovnat dva různé typy čísel, aniž by měnili jejich typy.|  
|[SafeModulus](../windows/safemodulus.md)|Provede operaci numerického zbytku na dvou čísel.|  
|[SafeMultiply](../windows/safemultiply.md)|Vynásobí dvě čísla společně a chrání před přetečení.|  
|[SafeSubtract](../windows/safesubtract.md)|Odečte dvou čísel a chrání před přetečení.|  
  
## <a name="related-sections"></a>Související oddíly  
  
|Část|Popis|  
|-------------|-----------------|  
|[SafeInt – třída](../windows/safeint-class.md)|`SafeInt` Třídy.|  
|[SafeIntException – třída](../windows/safeintexception-class.md)|Specifické pro knihovnu SafeInt třídou výjimky.|