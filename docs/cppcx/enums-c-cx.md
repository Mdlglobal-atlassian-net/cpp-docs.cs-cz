---
title: "Výčty (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d21a887c29b792b2857d0ee546dbc9722b60a264
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="enums-ccx"></a>Výčty (C + +/ CX)
C + +/ CX podporuje `public enum class` – klíčové slovo, což je analagous pro standardní C++ `scoped  enum`. Při použití enumerátor, který je deklarovaný s použitím `public enum class` – klíčové slovo, musíte použít identifikátor výčtu k určení rozsahu každou hodnotu výčtu.  
  
### <a name="remarks"></a>Poznámky  
 A `public enum class` , nemá specifikátor přístupu, jako například `public`, je považován za standardní C++ [obor výčtu](../cpp/enumerations-cpp.md).  
  
 A `public enum class` nebo `public enum struct` deklarace může mít typ základní integrální typu, i když prostředí Windows Runtime samotné vyžaduje, aby typu int32 nebo uint32 pro příkaz enum příznaky. Následující syntaxí popisuje části `public enum class` nebo `public enum struct`.  
  
 Tento příklad ukazuje, jak definovat veřejný výčet tříd:  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 Tento další příklad ukazuje, jak ho zpracovat:  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>Příklady  
 Další příklady ukazují, jak deklarovat výčet,  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 Další příklad ukazuje, jak převést na číselné ekvivalenty a provést porovnání. Všimněte si, že použití enumerátoru `One` je vymezeny `Enum1` identifikátor výčtu a enumerátor `First` je vymezeny `Enum2`.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)