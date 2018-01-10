---
title: "číselný (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: <cliext/numeric>
dev_langs: C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cdf9ccb65299af688fde2fbff7b3d6cedad6de96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)
Definuje kontejneru šablony funkce, které provádět algoritmy poskytuje pro číselné zpracování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <cliext/numeric>  
```  
  
## <a name="functions"></a>Funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](../dotnet/accumulate-stl-clr.md)|Vypočítá součet všech elementů v zadaném rozsahu včetně některé počáteční hodnoty tak, že vypočítá následných částečné součtů nebo vypočítá výsledek podobně získané z pomocí zadané operace binární než součet následných částečné výsledky.|  
|[adjacent_difference (STL/CLR)](../dotnet/adjacent-difference-stl-clr.md)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|  
|[inner_product (STL/CLR)](../dotnet/inner-product-stl-clr.md)|Vypočítá součet element-wise součin dvou rozsahy a přidává ji k zadaná počáteční hodnota nebo vypočítá výsledek obecný postup kde binárních operací sum a produktu jsou nahrazovány jiné zadaný binární operace.|  
|[partial_sum (STL/CLR)](../dotnet/partial-sum-stl-clr.md)|Vypočítá řadu součtů ve vstupní oblasti z první prvek prostřednictvím `i`element TD a ukládá výsledek každé součet v `i`element TD cílového rozsahu nebo vypočítá výsledek obecný postup kde operaci součet je nahrazena jinou zadaný binární operace.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo číselný >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)