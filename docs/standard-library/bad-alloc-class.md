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
ms.openlocfilehash: 0e76bd39477c92d075f1dba8cf14b912c0f616e0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955907"
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

[Exception – třída](../standard-library/exception-class.md) [bezpečnost vlákna ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
