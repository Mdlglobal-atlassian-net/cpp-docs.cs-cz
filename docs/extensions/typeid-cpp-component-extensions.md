---
title: typeid (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 8b22481fecb4b7de5106921fec1c3a43fab81a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181743"
---
# <a name="typeid--ccli-and-ccx"></a>typeid (C++/CLI a C++/CX)

Získá hodnotu, která označuje typ objektu.

> [!NOTE]
> Toto téma odkazuje na verzi C++ rozšíření typeid (Component Extensions). Verzi ISO C++ tohoto klíčového slova naleznete v tématu [Operátor typeid](../cpp/typeid-operator.md).

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
T::typeid
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Název typu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Název typu.

### <a name="remarks"></a>Poznámky

V C++/CX vrátí TypeId typ [Platform:: Type](../cppcx/platform-type-class.md) , který je vytvořen z informací o typu modulu runtime.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```
type::typeid
```

### <a name="parameters"></a>Parametry

*type*<br/>
Název typu (abstraktní deklarátor), pro který chcete objekt `System::Type`.

### <a name="remarks"></a>Poznámky

`typeid` slouží k získání <xref:System.Type> pro typ v době kompilace.

`typeid` je podobná získání systému:: Type v době běhu pomocí <xref:System.Type.GetType%2A> nebo <xref:System.Object.GetType%2A>. Identifikátor TypeId však jako parametr přijímá pouze název typu.  Pokud chcete použít instanci typu k získání svého systému:: název typu, použijte GetType.

`typeid` musí být schopné vyhodnotit název typu (Type) v době kompilace, zatímco GetType vyhodnocuje typ, který se má vrátit za běhu.

`typeid` může pro název nativního typu převzít název nativního typu nebo alias společného jazykového modulu runtime; Další informace naleznete v tématu [.NET Framework C++ ekvivalentyC++k nativním typům (/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) .

`typeid` také funguje s nativními typy, i když bude stále vracet System:: Type.  Chcete-li získat type_info strukturu, použijte [Operátor typeid](../cpp/typeid-operator.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad porovnává klíčové slovo typeid s `GetType()`m členem.

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

Následující příklad ukazuje, že proměnná typu System:: Type lze použít k získání atributů typu.  Také ukazuje, že pro některé typy bude nutné vytvořit typedef pro použití `typeid`.

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
