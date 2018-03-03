---
title: "funkční (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8e731767401964045307635a428d7606d628aca8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Zahrnout hlavičku STL/CLR `<cliext/functional>` k definování počtu tříd šablon a související šablony Delegáti a funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>Deklarace  
  
|Delegát|Popis|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|Delegát dva argument.|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|Delegát dva argument vrací `void`.|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|Delegát jeden argument.|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|Delegát jeden argument vrací `void`.|  
  
|Třída|Popis|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|Functor k negate functor dva argument.|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|Functor k vytvoření vazby první argument. argument dva functor.|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|Functor k vytvoření vazby druhý argument. argument dva functor.|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|Dělení functor.|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|Rovnat functor porovnání.|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|Větší functor porovnání.|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|Porovnání větší nebo rovna functor.|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|Menší functor porovnání.|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|Porovnání menší nebo rovna functor.|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|Logické a functor.|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|Logické není functor.|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|Logické nebo functor.|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|Odečtena functor.|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|MODULUS functor.|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|Vynásobte functor.|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|Functor vrátit argument Negované.|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|Není rovno porovnání functor.|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|Přidejte functor.|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|Functor k negate functor jeden argument.|  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|Generuje binder1st argument a functor.|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|Generuje binder2nd argument a functor.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Generuje unary_negate pro functor.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Generuje binary_negate pro functor.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / funkční >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)