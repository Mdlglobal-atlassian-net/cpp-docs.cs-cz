---
title: 'Postupy: Zachycení výjimek v nativním kódu vyvolaných z prostředí MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: c3afa29d8c9bee1c1f1cc2fd1869d108c08a249b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246681"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Postupy: Zachycení výjimek v nativním kódu vyvolaných z prostředí MSIL

V nativním kódu můžete zachytit nativní C++ výjimku z jazyka MSIL.  Výjimky CLR můžete zachytit pomocí `__try` a `__except`.

Další informace naleznete v tématu [strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md) a [moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example"></a>Příklad

Následující příklad definuje modul se dvěma funkcemi, jeden, který vyvolá nativní výjimku, a druhý, který vyvolá výjimku jazyka MSIL.

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

Následující příklad definuje modul, který zachytává nativní a výjimku jazyka MSIL.

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
