---
title: 'Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: d4e7ee1140942b0168c8ae94baabd938d6923c7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172241"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C++/CLI)

Funkce mohou být přetíženy v závislosti na tom, zda je typ parametru vnitřní ukazatel nebo nativní ukazatel.

> [!IMPORTANT]
> Tato funkce jazyka je podporována možností kompilátoru `/clr`, ale ne pomocí možnosti kompilátoru `/ZW`.

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
