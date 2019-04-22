---
title: Uživatelem definované operátory (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: cf80eb4c440c1308e8ea06a563c18569e4e4ddf2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774565"
---
# <a name="user-defined-operators-ccli"></a>Uživatelem definované operátory (C++/CLI)

Uživatelem definované operátory pro spravované typy jsou povoleny jako statické členy nebo členy instance nebo v globálním oboru. Nicméně pouze statické operátory jsou přístupné prostřednictvím metadat na klienty, kteří jsou napsané v jiném jazyce než v jazyce Visual C++.

Typ odkazu jeden z parametrů statické uživatelem definovaný operátor musí být jedna z následujících:

- Popisovač (`type` ^) na instanci nadřazeného typu.

- Dereference typu odkazu (`type`^ & nebo typ ^ %) ke zpracování do instance systému nadřazeného typu.

Typ hodnoty jeden z parametrů statické uživatelem definovaný operátor musí být jedna z následujících:

- Stejného typu jako nadřazený typ hodnoty.

- Dereference typu ukazatele (`type`^) do nadřazeného typu.

- Dereference typu odkazu (`type`% nebo `type`&) do nadřazeného typu.

- Dereference typu odkazu (`type`^ % nebo `type`^ &) pro popisovač.

Můžete definovat následující operátory:

|Operátor|Unární nebo binární formuláře?|
|--------------|--------------------------|
|!|Unární|
|!=|binární|
|%|binární|
|&|Jednočlenné a binární soubor|
|&&|binární|
|*|Jednočlenné a binární soubor|
|+|Jednočlenné a binární soubor|
|++|Unární|
|, |binární|
|-|Jednočlenné a binární soubor|
|--|Unární|
|->|Unární|
|/|binární|
|<|binární|
|<<|binární|
|\<=|binární|
|=|binární|
|==|binární|
|>|binární|
|>=|binární|
|>>|binární|
|^|binární|
|false|Unární|
|true|Unární|
|&#124;|binární|
|&#124;&#124;|binární|
|~|Unární|

## <a name="example"></a>Příklad

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>Příklad

Následující příklad ukazuje syntéze operátoru, který je k dispozici pouze při použití **/CLR** ke kompilaci. Syntéze operátoru vytvoří formulář přiřazení binárního operátoru, pokud není definována, pokud levá strana operátoru přiřazení s typem CLR.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
