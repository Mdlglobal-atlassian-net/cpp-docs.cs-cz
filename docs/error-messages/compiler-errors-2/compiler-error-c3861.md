---
title: Chyba kompilátoru C3861
ms.date: 03/23/2018
f1_keywords:
- C3861
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
ms.openlocfilehash: 4ebfd3b0129e25cf543cac803a3b33fb074f3d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302408"
---
# <a name="compiler-error-c3861"></a>Chyba kompilátoru C3861

> "*identifikátor*': identifikátor se nenašel

Kompilátor se nepodařilo přeložit odkaz na identifikátor rozhraní i pomocí vyhledávání závislého na argumentu.

## <a name="remarks"></a>Poznámky

Chcete-li tuto chybu opravit, porovnejte použití *identifikátor* identifikátor deklarace pro případ a kontrolu pravopisu. Ověřte, že [oboru rozlišení operátory](../../cpp/scope-resolution-operator.md) a obor názvů [direktiv using](../../cpp/namespaces-cpp.md#using_directives) správné použití. Pokud identifikátor je deklarována v souboru hlaviček, ověřte, že záhlaví zahrnuté předtím, než se odkazuje identifikátor. Pokud se bude externě viditelného identifikátoru, ujistěte se, že je deklarována v libovolného zdrojového souboru, která ji používá. Zkontrolujte také, že identifikátor deklarace nebo definice není vyloučený podle [direktivy podmíněné kompilace](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

Odebrat zastaralé funkce běhové knihovny jazyka C v sadě Visual Studio 2015 změny mohou způsobit C3861. Chcete-li vyřešit tuto chybu, odeberte odkazy na tyto funkce nebo je nahradit zabezpečené alternativy, pokud existuje. Další informace najdete v tématu [zastaralé funkce](../../c-runtime-library/obsolete-functions.md).

Pokud se zobrazí chyba C3861 po dokončení migrace projektu ze starších verzí kompilátoru, můžete mít problémy související s podporovanou verzí Windows. Jazyk Visual C++ již podporuje cílení na Windows 95, Windows 98, Windows ME, Windows NT nebo Windows 2000. Pokud vaše **WINVER** nebo **_WIN32_WINNT** makra se přiřadí k jednomu z těchto verzí systému Windows, je třeba upravit makra. Další informace najdete v tématu [úpravy WINVER a _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).

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

Následující ukázka generuje C3861, protože identifikátor je zobrazen v rozsahu souboru definice, pouze pokud je deklarovaná v jiných zdrojových souborech, které ji používají.

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

### <a name="namespace-qualification-required"></a>Kvalifikace Namespace vyžaduje

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

### <a name="obsolete-function-called"></a>Zastaralé funkce, které volá

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

### <a name="adl-and-friend-functions"></a>ADL a Friend – funkce

Následující ukázka generuje C3767, protože kompilátor nemůže použít argument vyhledávání závislé `FriendFunc`:

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

Chcete-li chybu opravit, deklarujte přítele v rozsahu třídy a definujte jej v oboru názvů:

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
