---
title: 'Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C + +/ CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: bd2bc59d85854dedd0f1a349885312d4346aa925
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787008"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C + +/ CLI)

Funkce mohou být přetíženy podle toho, zda je typ parametru vnitřní ukazatel nebo nativní ukazatel.

> [!IMPORTANT]
> Této funkci jazyka podporuje `/clr` – možnost kompilátoru, ale ne za `/ZW` – možnost kompilátoru.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>Viz také

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)