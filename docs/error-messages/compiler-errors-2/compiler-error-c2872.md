---
title: "C2872 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2872
dev_langs: C++
helpviewer_keywords: C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 03bfb79a424b1272239826abf3056a8ab6228eec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2872"></a>C2872 chyby kompilátoru
'*symbol*': nejednoznačný – symbol  
  
Kompilátor nemůže určit, který symbol jsou odkazy na. Více než jeden symbol se zadaným názvem se nachází v oboru. Najdete v poznámkách k následující chybová zpráva pro umístění souborů a deklarace kompilátoru pro nejednoznačný symbol nalezen. Chcete-li tento problém vyřešit, můžete pomocí jeho obor názvů, například plnému určení nejednoznačný symbol `std::byte` nebo `::byte`. Můžete použít také [alias oboru názvů](../../cpp/namespaces-cpp.md#namespace_aliases) přiřadit součástí oboru názvů pohodlný krátký název pro použití při nejednoznačnosti symboly ve zdrojovém kódu.  
  
C2872 může dojít, pokud obsahuje soubor hlaviček [using – direktiva](../../cpp/namespaces-cpp.md#using_directives), a následné hlavička souboru je součástí obsahující typ, který je taky v zadané v oboru názvů `using` – direktiva. Zadejte `using` direktivy až po všechny vaše soubory hlaviček nejsou zadány s `#include`.  
  
 Další informace o C2872, najdete v článcích znalostní báze Knowledge Base [PRB: kompilátoru chyby při použijete #import s XML v aplikaci Visual C++ .NET](http://support.microsoft.com/kb/316317) a ["C2872 Chyba: 'Platformy': nejednoznačný symbol" chybová zpráva při použití Obor názvů Windows::Foundation::metadata v sadě Visual Studio 2013](https://support.microsoft.com/kb/2890859).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2872, protože dvojznačný odkaz Přišla žádost o proměnné s názvem `i`; dvě proměnné se stejným názvem jsou v oboru:  
  
```cpp  
// C2872.cpp  
// compile with: cl /EHsc C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok, uses i from global namespace  
   A::i++;   // ok, uses i from namespace A  
   i++;   // C2872 ambiguous: ::i or A::i? 
   // To fix this issue, use the fully qualified name
   // for the intended variable. 
}  
```