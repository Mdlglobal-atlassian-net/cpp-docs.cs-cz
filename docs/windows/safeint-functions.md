---
title: SafeInt – Functions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions, SafeInt
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8a0475b5d3ba9053cd5d2df5ffd99ce9292ba8e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603452"
---
# <a name="safeint-functions"></a>Funkce jazyka SafeInt
SafeInt – knihovna poskytuje několik funkcí, které lze použít bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md). Pokud chcete zabránit přetečení celého čísla jedné matematické operace, můžete tyto funkce. Pokud chcete chránit několik matematických operací, měli byste vytvořit **SafeInt** objekty. Je mnohem efektivnější, chcete-li vytvořit **SafeInt** objektů, než se tyto funkce používat více než jednou.  
  
 Tyto funkce umožňují snadno porovnat nebo provádění matematických operací na dva různé typy parametrů, aniž by bylo nutné je nejprve převést na stejný typ.  
  
 Každá z těchto funkcí má dva typy šablon: `T` a `U`. Každý z těchto typů může být logická hodnota, znak nebo celočíselného typu. Integrální typy mohou být podepsaný nebo nepodepsaný řetězec a libovolné velikosti z 8 bitů na 64 bitů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SafeAdd](../windows/safeadd.md)|Sečte dvě čísla a chrání proti přetečení.|  
|[SafeCast](../windows/safecast.md)|Přetypování jednoho typu na jiný typ parametru.|  
|[SafeDivide](../windows/safedivide.md)|Provede podíl dvou čísel a chrání proti dělení nulou.|  
|[SafeEquals](../windows/safeequals.md), [SafeGreaterThan](../windows/safegreaterthan.md), [SafeGreaterThanEquals](../windows/safegreaterthanequals.md), [SafeLessThan](../windows/safelessthan.md), [SafeLessThanEquals](../windows/safelessthanequals.md), [ SafeNotEquals](../windows/safenotequals.md)|Porovná dvě čísla. Tyto funkce umožňují snadno porovnat dva různé typy čísel beze změny jejich typy.|  
|[SafeModulus](../windows/safemodulus.md)|Provádí operace numerického zbytku dvou čísel.|  
|[SafeMultiply](../windows/safemultiply.md)|Vynásobí dvě čísla společně a chrání proti přetečení.|  
|[SafeSubtract](../windows/safesubtract.md)|Odečte dvou čísel a chrání proti přetečení.|  
  
## <a name="related-sections"></a>Související oddíly  
  
|Oddíl|Popis|  
|-------------|-----------------|  
|[SafeInt – třída](../windows/safeint-class.md)|**SafeInt** třídy.|  
|[SafeIntException – třída](../windows/safeintexception-class.md)|Třídy výjimek specifické pro SafeInt – knihovna.|