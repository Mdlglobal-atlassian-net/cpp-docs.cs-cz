---
title: bad_alloc – třída
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 63b474d0209a5cc385de9dc11b56d5de8382a9cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376416"
---
# <a name="badalloc-class"></a>bad_alloc – třída

Tato třída popisuje výjimku vyvolanou k označení, že požadavek na přidělení nebylo úspěšné.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená `what` je řetězec C definované implementací. Žádná z členské funkce generovat žádné výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

**Namespace:** std

## <a name="example"></a>Příklad

```cpp
// bad_alloc.cpp
// compile with: /EHsc
#include<new>
#include<iostream>
using namespace std;

int main() {
   char* ptr;
   try {
      ptr = new char[(~unsigned int((int)0)/2) - 1];
      delete[] ptr;
   }
   catch( bad_alloc &ba) {
      cout << ba.what( ) << endl;
   }
}
```

## <a name="sample-output"></a>Vzorový výstup

```Output
bad allocation
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

## <a name="see-also"></a>Viz také:

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
