---
title: bad_alloc – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 571885410363aee55d15e68b81ba4fd9e2b8e54b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705585"
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

## <a name="see-also"></a>Viz také

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
