---
title: Subscripting | Microsoft Docs
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
ms.openlocfilehash: 65798eb9983273cf3b8b2b136be9a9acc082cb4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="subscripting"></a>Předplatné
Operátor dolního indexu (**[]**), například operátor volání funkce, je považován za binární operátor. Operátor dolního indexu musí být nestatické členské funkce, která přebírá jeden argument. Tento argument může být jakéhokoli typu, která označuje dolní index požadované pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vektoru typu `int` , která implementuje hranice kontrola:  
  
```  
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
 Když `i` dosáhne 10 v předchozím programu `operator[]` zjistí, že out-of-bounds dolního indexu je používán a vydá chybovou zprávu.  
  
 Všimněte si, že funkce `operator[]` vrátí odkazového typu. To způsobí, že bude l hodnota, což umožňuje použití dolního indexu výrazů na žádné straně operátorů přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)