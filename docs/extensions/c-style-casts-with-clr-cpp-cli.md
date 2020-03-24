---
title: Přetypování ve stylu C pomocí-CLR (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: 2b7e492c62047e3b38224637f842d8a7fcbae84f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172591"
---
# <a name="c-style-casts-with-clr-ccli"></a>Přetypování ve stylu jazyka pomocí možnosti /clr (C++/CLI)

Následující téma se vztahuje pouze na modul CLR (Common Language Runtime).

Při použití s typy CLR se kompilátor pokusí mapovat přetypování ve stylu jazyka C na jedno z přetypování uvedených níže v tomto pořadí:

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

Pokud žádná z přetypování uvedená výše není platná, a pokud typ výrazu a cílový typ jsou odkazy na CLR, přetypování ve stylu jazyka C mapuje na modul runtime-check (instrukce Castclass MSIL). V opačném případě přetypování ve stylu jazyka C je považováno za neplatné a kompilátor vydá chybu.

## <a name="remarks"></a>Poznámky

Přetypování ve stylu jazyka C se nedoporučuje. Při kompilaci s možností [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)použijte [safe_cast](safe-cast-cpp-component-extensions.md).

Následující příklad ukazuje přetypování ve stylu jazyka C, které je mapováno na **const_cast**.

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

Následující příklad ukazuje přetypování ve stylu jazyka C, které je mapováno na **safe_cast**.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

Následující příklad ukazuje přetypování ve stylu jazyka C, které se mapuje na **safe_cast** a **const_cast**.

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

Následující příklad ukazuje přetypování ve stylu jazyka C, které je mapováno na **static_cast**.

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

Následující příklad ukazuje přetypování ve stylu jazyka C, které se mapuje na **static_cast** a **const_cast**.

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

Následující příklad ukazuje přetypování ve stylu jazyka C, které se mapuje na kontrolu za běhu.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

Následující příklad ukazuje neplatné přetypování ve stylu jazyka C, které způsobí, že kompilátor vydá chybu.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
