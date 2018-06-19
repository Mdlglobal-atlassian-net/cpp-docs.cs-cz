---
title: Iterování přes kolekci knihoven C++ Standard pomocí pro každou | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DTL collections, iterating over
ms.assetid: 9358ca29-b982-4a19-bbfd-bef50fe66c9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 963c8a4213da756f03e95924940dc179bd305f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131339"
---
# <a name="iterating-over-c-standard-library-collection-by-using-for-each"></a>Iterování přes kolekci knihoven C++ Standard pomocí pro každou
`for each` – Klíčové slovo lze použít k iteraci přes kolekci standardní knihovna C++.  
  
## <a name="all-platforms"></a>Všechny platformy  
 **Poznámky**  
  
 Standardní knihovna C++ kolekce je také označován jako *kontejneru*. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).  
  
## <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu používá `for each` Iterujte přes [ \<mapy >](../standard-library/map.md).  
  
```  
// for_each_stl.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
using namespace std;  
  
int main() {  
   int retval  = 0;  
   map<string, int> months;  
  
   months["january"] = 31;  
   months["february"] = 28;  
   months["march"] = 31;  
   months["april"] = 30;  
   months["may"] = 31;  
   months["june"] = 30;  
   months["july"] = 31;  
   months["august"] = 31;  
   months["september"] = 30;  
   months["october"] = 31;  
   months["november"] = 30;  
   months["december"] = 31;  
  
   map<string, int> months_30;  
  
   for each( pair<string, int> c in months )  
      if ( c.second == 30 )  
         months_30[c.first] = c.second;  
  
   for each( pair<string, int> c in months_30 )  
      retval++;  
  
   cout << "Months with 30 days = " << retval << endl;  
}  
```  
  
 **Output**  
  
```Output  
Months with 30 days = 4  
```  
  
 **Příklad**  
  
 Následující příklad kódu používá const odkaz (`const&`) pro proměnnou iterace s kontejnery standardní knihovna C++. Můžete použít odkaz (`&`) jako na proměnnou iterace na jakoukoli kolekci, typu, který lze deklarovat jako *T*`&`.  
  
```  
// for_each_stl_2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
using namespace std;  
  
int main() {  
   int retval = 0;  
  
   vector<int> col(3);  
   col[0] = 10;  
   col[1] = 20;  
   col[2] = 30;  
  
   for each( const int& c in col )  
      retval += c;  
  
   cout << "retval: " << retval << endl;  
}  
```  
  
 **Output**  
  
```Output  
retval: 60  
```  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 Neexistují žádné specifické pro platformu poznámky o této funkci.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 Neexistují žádné specifické pro platformu poznámky o této funkci.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
## <a name="see-also"></a>Viz také  
 [pro každou v](../dotnet/for-each-in.md)   
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)