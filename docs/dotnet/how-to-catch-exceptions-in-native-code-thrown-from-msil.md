---
title: 'Postupy: Zachycení výjimek v nativním kódu vyvolaných z prostředí MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 95ce7a2afabc34ea78376b12da61f419dab4af34
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776554"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Postupy: Zachycení výjimek v nativním kódu vyvolaných z prostředí MSIL

V nativním kódu můžete zachytit nativní výjimek jazyka C++ z prostředí MSIL.  Při zachycení výjimky CLR s `__try` a `__except`.

Další informace najdete v tématu [strukturovaného zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md) a [zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md).

## <a name="example"></a>Příklad

Následující příklad definuje dvě funkce, ten, který vyvolá výjimky na nativní a další modul, který vyvolá výjimku jazyka MSIL.

```
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>Příklad

Následující příklad definuje modul, který zachytí nativní a výjimky jazyka MSIL.

```
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../extensions/exception-handling-cpp-component-extensions.md)
