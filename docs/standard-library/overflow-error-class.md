---
title: overflow_error – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::overflow_error
dev_langs:
- C++
helpviewer_keywords:
- overflow_error class
ms.assetid: bae7128d-e36b-4a45-84f1-2f89da441d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3bf0073c5f6f1acc574ca49b116513046337aaf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="overflowerror-class"></a>overflow_error – třída

Třída slouží jako základní třída pro všechny výjimky vydané nahlásit aritmetického přetečení.

## <a name="syntax"></a>Syntaxe

```cpp
class overflow_error : public runtime_error {
public:
    explicit overflow_error(const string& message);

    explicit overflow_error(const char *message);

};
```

## <a name="remarks"></a>Poznámky

Hodnoty vrácené [co](../standard-library/exception-class.md) je kopie **zpráva**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Příklad

```cpp
// overflow_error.cpp
// compile with: /EHsc /GR
#include <bitset>
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      bitset< 33 > bitset;
      bitset[32] = 1;
      bitset[0] = 1;
      unsigned long x = bitset.to_ulong( );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
\* Output:
Caught bitset<N> overflow
Type class std::overflow_error
*\
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<stdexcept – >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[runtime_error – třída](../standard-library/runtime-error-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
