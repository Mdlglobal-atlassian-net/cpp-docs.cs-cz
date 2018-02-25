---
title: random_access_iterator_tag Struct | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xutility/std::random_access_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- random_access_iterator_tag class
- random_access_iterator_tag struct
ms.assetid: 59f5b741-c5b4-459c-ad0a-3b67cddeea23
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b18916b4842bcb7b52f79fe5c0b92965043040
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="randomaccessiteratortag-struct"></a>random_access_iterator_tag – struktura
Třídu, která poskytuje návratový typ pro **iterator_category –** funkce, která představuje iterator náhodný přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct random_access_iterator_tag    : public bidirectional_iterator_tag {};
```  
  
## <a name="remarks"></a>Poznámky  
 Třídy značky kategorie se používají jako zkompilovat značky pro výběr algoritmů. Funkce šablony musí najít nejvíce určitou kategorii její argument iterator tak, aby v době kompilace může použít algoritmus maximální efektivitou. Pro každý iterator typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category –** musí být definován jako nejvíce značky kategorii, která popisuje iteraci chování.  
  
 Typ je stejný jako **iterator** \< **Iter**> **:: iterator_category –** při **Iter** popisuje objekt, který může sloužit jako iterator náhodný přístup.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// iterator_rait.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <list>  
  
using namespace std;  
  
int main( )  
{  
   vector<int> vi;  
   vector<char> vc;  
   list<char> lc;  
   iterator_traits<vector<int>:: iterator>::iterator_category cati;  
   iterator_traits<vector<char>:: iterator>::iterator_category catc;  
   iterator_traits<list<char>:: iterator>::iterator_category catlc;  
  
   // These are both random-access iterators  
   cout << "The type of iterator for vector<int> is "  
       << "identified by the tag:\n "   
       << typeid ( cati ).name( ) << endl;  
   cout << "The type of iterator for vector<char> is "  
       << "identified by the tag:\n "   
       << typeid ( catc ).name( ) << endl;  
   if ( typeid ( cati ) == typeid( catc ) )  
      cout << "The iterators are the same." << endl << endl;  
   else  
      cout << "The iterators are not the same." << endl << endl;  
  
   // But the list iterator is bidirectinal, not random access  
   cout << "The type of iterator for list<char> is "  
       << "identified by the tag:\n "   
       << typeid (catlc).name( ) << endl;  
  
   // cout << ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) ) << endl;  
   if ( typeid ( vi.begin( ) ) == typeid( vc.begin( ) ) )  
      cout << "The iterators are the same." << endl;  
   else  
      cout << "The iterators are not the same." << endl;  
   // A random-access iterator is a bidirectional iterator.  
   cout << ( void* ) dynamic_cast< iterator_traits<list<char>:: iterator>  
          ::iterator_category* > ( &catc ) << endl;  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
 Pro x86 je následující výstup.  
  
```
The type of iterator for vector<int> is identified by the tag:
    struct std::random_access_iterator_tag
The type of iterator for vector<char> is identified by the tag:
    struct std::random_access_iterator_tag
The iterators are the same.

The type of iterator for list<char> is identified by the tag:
    struct std::bidirectional_iterator_tag
The iterators are not the same.
0012FF3B
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [bidirectional_iterator_tag Struct](../standard-library/bidirectional-iterator-tag-struct.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



