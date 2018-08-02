---
title: Subscripting | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c278c39908312f76a8b62a529beaed884c07a81d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461517"
---
# <a name="subscripting"></a>Předplatné
Operátor dolního indexu (**[] č.**), třeba operátor volání funkce se považuje za binární operátor. Operátor dolního indexu musí být nestatickou členskou funkci, která přijímá jeden argument. Tento argument může být libovolného typu a Určuje dolní index požadované pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vektorového typu **int** , která implementuje ověřování hranic:  
  
```cpp 
// subscripting.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class IntVector {  
public:  
   IntVector( int cElements );  
   ~IntVector() { delete [] _iElements; }  
   int& operator[](int nSubscript);  
private:  
   int *_iElements;  
   int _iUpperBound;  
};  
  
// Construct an IntVector.  
IntVector::IntVector( int cElements ) {  
   _iElements = new int[cElements];  
   _iUpperBound = cElements;  
}  
  
// Subscript operator for IntVector.  
int& IntVector::operator[](int nSubscript) {  
   static int iErr = -1;  
  
   if( nSubscript >= 0 && nSubscript < _iUpperBound )  
      return _iElements[nSubscript];  
   else {  
      clog << "Array bounds violation." << endl;  
      return iErr;  
   }  
}  
  
// Test the IntVector class.  
int main() {  
   IntVector v( 10 );  
   int i;  
  
   for( i = 0; i <= 10; ++i )  
      v[i] = i;  
  
   v[3] = v[9];  
  
   for ( i = 0; i <= 10; ++i )  
      cout << "Element: [" << i << "] = " << v[i] << endl;  
}  
```  
  
```Output  
Array bounds violation.  
Element: [0] = 0  
Element: [1] = 1  
Element: [2] = 2  
Element: [3] = 9  
Element: [4] = 4  
Element: [5] = 5  
Element: [6] = 6  
Element: [7] = 7  
Element: [8] = 8  
Element: [9] = 9  
Array bounds violation.  
Element: [10] = 10  
```  
  
## <a name="comments"></a>Komentáře  
 Když `i` dosáhne 10 v předchozí program **operator []** zjistí, že celočíselných dolního indexu se používá a vydává chybovou zprávu.  
  
 Všimněte si, že funkce **operator []** vrací typ reference. To vede k jejímu l hodnotou, je možné využívat indexovaný výrazů na obou stranách operátory přiřazení.  
  
## <a name="see-also"></a>Viz také:  
 [Přetížení operátoru](../cpp/operator-overloading.md)