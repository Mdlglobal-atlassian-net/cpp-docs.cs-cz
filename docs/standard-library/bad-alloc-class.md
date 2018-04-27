---
title: bad_alloc – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ccff017974b0f813b1c8d2212b6cc981f968bc8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
