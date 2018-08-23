---
title: Výčty (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e2b9edb7ba2a84418e900ffb1aafe4c5064af
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593961"
---
# <a name="enums-ccx"></a>Výčty (C + +/ CX)
C + +/ CX podporuje `public enum class` – klíčové slovo, což je standard c++ analagous `scoped  enum`. Při použití enumerátor, který je deklarovaná příkazem using `public enum class` – klíčové slovo, identifikátor výčtu musíte použít k určení rozsahu každá hodnota výčtu.  
  
### <a name="remarks"></a>Poznámky  
 A `public enum class` , který neobsahuje specifikátor přístupu, jako například `public`, je považován za standardní C++ [rozsah výčtu](../cpp/enumerations-cpp.md).  
  
 A `public enum class` nebo `public enum struct` deklarace může mít základní typ libovolný integrální typ, i když samotný modul Runtime Windows vyžaduje, aby typ int32 nebo uint32 pro výčet příznaků. Následující syntaxe popisuje části `public enum class` nebo `public enum struct`.  
  
 Tento příklad ukazuje, jak definovat veřejný výčet tříd:  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 Tento další příklad ukazuje, jak použít:  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>Příklady  
 Další příklady ukazují, jak deklarovat výčet,  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 Následující příklad ukazuje, jak převést na číselnou ekvivalenty a provést porovnání. Všimněte si, že užívání výčet `One` je určeno `Enum1` identifikátor výčtu a enumerátor `First` je určeno `Enum2`.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)