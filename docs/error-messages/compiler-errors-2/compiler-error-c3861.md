---
title: C3861 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 03/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- C3861
dev_langs:
- C++
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afe6a83e2dad9b836fdd602aca98fb9f20b89a62
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="compiler-error-c3861"></a>Compiler Error C3861

> '*identifikátor*': nebyl nalezen identifikátor

Kompilátor nebylo možné přeložit odkaz na identifikátor, i pomocí vyhledávání závislého na argumentu.

## <a name="remarks"></a>Poznámky

Chcete-li tuto chybu opravit, porovnejte použití *identifikátor* identifikátor deklaraci pro případ a pravopis. Ověřte, že [oboru rozlišení operátory](../../cpp/scope-resolution-operator.md) a obor názvů [pomocí direktiv](../../cpp/namespaces-cpp.md#using_directives) používají správně. Pokud je identifikátor deklarován v záhlaví souboru, ověření hlavičku zahrnuté před identifikátor odkazuje. Pokud identifikátor měl by být externě viditelné, ujistěte se, že je deklarovaná ve zdrojovém souboru, který se používá. Také zkontrolujte, jestli není vyloučený identifikátor deklarace a definice [Podmíněná kompilace direktivy](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Změny k odebrání zastaralé funkce běhové knihovny jazyka C v sadě Visual Studio 2015 může způsobit C3861. Chcete-li tuto chybu vyřešit, odebrat odkazy na tyto funkce nebo je nahradit jejich zabezpečený alternativy, pokud existuje. Další informace najdete v tématu [zastaralé funkce](../../c-runtime-library/obsolete-functions.md).

Pokud se zobrazí chyba C3861 po migraci projektu ze starších verzí kompilátor, můžete mít problémy související s podporovanou verzí Windows. Visual C++ již nepodporuje cílení systému Windows 95, Windows 98, Windows ME, Windows NT nebo Windows 2000. Pokud vaše **WINVER** nebo **_WIN32_WINNT** makra se přiřadí k jednomu z těchto verzí systému Windows, musíte upravit makra. Další informace najdete v tématu [úprava WINVER a _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

## <a name="examples"></a>Příklady

### <a name="undefined-identifier"></a>Nedefinovaný identifikátor

Následující ukázka generuje C3861, protože identifikátor není definován.

```cpp
// C3861.cpp
void f2(){}
int main() {
   f();    // C3861
   f2();   // OK
}
```

### <a name="identifier-not-in-scope"></a>Identifikátor není v oboru

Následující ukázka generuje C3861, protože identifikátor je viditelné v oboru souboru jeho definice, pouze pokud je deklarovaná v jiné zdrojové soubory, které ho používají.

```cpp
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {
   std::cout << f() << std::endl;    // C3861
}
```

```cpp
// C3861_a2.cpp
int f() {  // declared and defined here
   return 42;
}
```

### <a name="namespace-qualification-required"></a>Kvalifikace Namespace požadované

Třídy výjimek ve standardní knihovně C++ vyžadují `std` oboru názvů.

```cpp
// C3861_b.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   try {
      throw exception("Exception");   // C3861
      // try the following line instead
      // throw std::exception("Exception");
   }
   catch (...) {
      std::cout << "caught an exception" << std::endl;
   }
}
```

### <a name="obsolete-function-called"></a>Volaná zastaralé funkce

Zastaralé funkce byly odebrány z knihovny CRT.

```cpp
// C3861_c.cpp
#include <stdio.h>
int main() {
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C3861
   // Use gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

### <a name="adl-and-friend-functions"></a>Funkce ADL a friend

Následující ukázka generuje C3767, protože kompilátor nelze použít argument závislé vyhledávání pro `FriendFunc`:

```cpp
namespace N {
   class C {
      friend void FriendFunc() {}
      friend void AnotherFriendFunc(C* c) {}
   };
}

int main() {
   using namespace N;
   FriendFunc();   // C3861 error
   C* pC = new C();
   AnotherFriendFunc(pC);   // found via argument-dependent lookup
}
```

Opravte chybu, deklarovat friend v rozsahu třídy a definovat v oboru názvů:

```cpp
class MyClass {
   int m_private;
   friend void func();
};

void func() {
   MyClass s;
   s.m_private = 0;
}

int main() {
   func();
}
```
