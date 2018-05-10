---
title: bad_alloc – třída | Microsoft Docs
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
ms.openlocfilehash: 9ab496a5de8062f6888b92b318788ff72345bc7c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="badalloc-class"></a>bad_alloc – třída

Třída popisuje výjimka vyvolaná indikující, že žádost o přidělení nebylo úspěšné.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>Poznámky

Hodnoty vrácené **co** je řetězec definované implementací C. Žádná z členské funkce throw jakékoli výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

**Namespace:** – std

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

[Třída Exception](../standard-library/exception-class.md) [bezpečný přístup z více vláken ve standardní knihovna C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
