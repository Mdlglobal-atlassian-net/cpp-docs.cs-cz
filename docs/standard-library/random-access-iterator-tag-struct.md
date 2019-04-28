---
title: random_access_iterator_tag – struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::random_access_iterator_tag
helpviewer_keywords:
- random_access_iterator_tag class
- random_access_iterator_tag struct
ms.assetid: 59f5b741-c5b4-459c-ad0a-3b67cddeea23
ms.openlocfilehash: 81e958750ab13c12e92b61e6971c40f3362ba22d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369875"
---
# <a name="randomaccessiteratortag-struct"></a>random_access_iterator_tag – struktura

Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor náhodného přístupu.

## <a name="syntax"></a>Syntaxe

```cpp
struct random_access_iterator_tag    : public bidirectional_iterator_tag {};
```

## <a name="remarks"></a>Poznámky

Kategorie značky tříd se používají při kompilaci značky pro algoritmus výběru. Funkce šablony musí najít nejspecifičtější kategorie svůj argument iterátoru tak, aby ho používat co nejúčinnější algoritmus v době kompilace. Pro každý iterátor typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musí být definovány nejspecifičtější značky kategorii, která popisuje chování iterátoru.

Typ je stejný jako **iterátoru** \< **Iter**> **:: iterator_category** při `Iter` popisuje objekt, který může sloužit jako iterátor s náhodným přístupem.

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

Následující výstup je pro x86.

```Output
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

**Záhlaví:** \<iterátor >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[bidirectional_iterator_tag – struktura](../standard-library/bidirectional-iterator-tag-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
