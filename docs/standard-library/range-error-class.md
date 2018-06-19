---
title: range_error – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::range_error
dev_langs:
- C++
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63d6497dda220723587623cb42551366ddcbef80
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853083"
---
# <a name="rangeerror-class"></a>range_error – třída

Třída slouží jako základní třída pro všechny výjimky vydané rozsah chybové zprávě.

## <a name="syntax"></a>Syntaxe

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);

    explicit range_error(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnoty vrácené [co](../standard-library/exception-class.md) je kopie **zpráva**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Příklad

```cpp
// range_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;
int main()
{
   try
   {
      throw range_error( "The range is in error!" );
   }
   catch (exception &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
\* Output:
Caught: The range is in error!
Type: class std::range_error
*\
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<stdexcept – >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[runtime_error – třída](../standard-library/runtime-error-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
