---
title: typeid (C + +/ CLI a C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1196956208d490674d4705a8d1e61ea3381d94a2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065184"
---
# <a name="typeid--ccli-and-ccx"></a>typeid (C + +/ CLI a C + +/ CX)

Získá hodnotu, která určuje typ objektu.

> [!NOTE]
> Toto téma odkazuje na verzi rozšíření komponent C++ typeid. Verzi tohoto klíčového slova ISO C++ naleznete v části [typeid – operátor](../cpp/typeid-operator.md).

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
T::typeid
```

### <a name="parameters"></a>Parametry

*T*<br/>
Název typu.

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Název typu.

### <a name="remarks"></a>Poznámky

V jazyce C + +/ CX, vrátí typeid [Platform::type –](../cppcx/platform-type-class.md) , který je vytvořen z informací o typu modulu runtime.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```
type::typeid
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Název typu (abstraktní deklarátor), pro které chcete `System::Type` objektu.

### <a name="remarks"></a>Poznámky

`typeid` slouží k získání <xref:System.Type> pro typ v době kompilace.

`typeid` je podobný System::Type typu za běhu pomocí <xref:System.Type.GetType%2A> nebo <xref:System.Object.GetType%2A>. Typeid však přijímá pouze název typu jako parametr.  Pokud chcete získat jeho název System::Type pomocí instance typu, použijte GetType.

`typeid` musí mít k vyhodnocení názvu typu (typ) v době kompilace, zatímco GetType vyhodnocen jako typ určený k vrácení v době běhu.

`typeid` může trvat nativní typ název nebo common language runtime alias pro nativní typ name; Zobrazit [rozhraní .NET Framework – ekvivalenty nativních typů C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) Další informace.

`typeid` taky spolupracuje s nativní typy, i když stále vrátí System::Type.  Type_info – struktura, použijte [typeid – operátor](../cpp/typeid-operator.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad porovnává typeid – klíčové slovo chcete `GetType()` člena.

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

Následující příklad ukazuje, že proměnné typu System::Type je možné získat atributy typu.  Profil také ukazuje, že u některých typů, budete muset vytvořit definice typu použití `typeid`.

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

[Přípony komponent pro .NET a UPW](../windows/component-extensions-for-runtime-platforms.md)