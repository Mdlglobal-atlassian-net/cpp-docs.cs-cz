---
title: Optimalizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8222d909ad23157b4e3ed32a6920abadd77709b6
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466303"
---
# <a name="optimize"></a>optimize
Určuje optimalizace, které provádí na základě funkce funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Poznámky  

**Optimalizovat** – Direktiva pragma musí být uvedena mimo funkci a na první funkci definovanou po viděli direktivy pragma se projeví. *Na* a *vypnout* argumenty zapnutí možnosti zadané v *seznamu optimalizací* zapnutí nebo vypnutí.  
  
*Seznamu optimalizací* může být nula nebo více parametrů je znázorněno v následující tabulce.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parametry optimize – direktiva Pragma  
  
|Parametry|Typ optimalizace|  
|--------------------|--------------------------|  
|*g*|Povolte globální optimalizace.|  
|*s* nebo *t*|Zadejte krátký nebo rychlý sekvence strojového kódu.|  
|*y*|Generovat ukazatelů rámců v zásobníku programu.|  
  
Toto jsou stejná písmena použít s [/O](../build/reference/o-options-optimize-code.md) – možnosti kompilátoru. Například následující direktivu pragma je ekvivalentní `/Os` – možnost kompilátoru:  
  
```  
#pragma optimize( "ts", on )  
```  
  
Použití **optimalizovat** – Direktiva pragma se prázdný řetězec (**""**) je zvláštní forma direktivy:  
  
Při použití *vypnout* parametr, zapne optimalizace, které jsou uvedené v tabulce výše v tomto tématu, vypnout.  
  
Při použití *na* parametr resetuje optimalizace na ty, které jste zadali pomocí [/O](../build/reference/o-options-optimize-code.md) – možnost kompilátoru.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)