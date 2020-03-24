---
title: Předplatné
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 8974f6619af462050fc8a02798fe44007ea928e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160889"
---
# <a name="subscripting"></a>Předplatné

Operátor dolního indexu ( **[]** ), jako je operátor volání funkce, je považován za binární operátor. Operátor dolního indexu musí být nestatická členská funkce, která přijímá jeden argument. Tento argument může být libovolného typu a určuje požadovaný dolní index pole.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit vektor typu **int** , který implementuje kontrolu hranic:

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

Když `i` dosáhne 10 v předchozím programu, **operátor []** zjistí, že je použit dolní index, který je používán, a vydá chybovou zprávu.

Všimněte si, že **operátor funkce []** vrátí typ odkazu. Způsobí to, že se jedná o l-hodnotu, což vám umožní používat na obou stranách operátorů přiřazení výrazy s indexy.

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
