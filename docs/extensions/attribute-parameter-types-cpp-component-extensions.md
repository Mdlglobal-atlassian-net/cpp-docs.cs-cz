---
title: Typy parametrů atributů (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
ms.openlocfilehash: fbb2bd68f589630608e341b944b4201c12d67211
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041316"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>Typy parametrů atributů (C++vyhodnocovací a C++/CX)

Hodnoty předané metodě atributy musí být známo pro kompilátor v době kompilace.  Parametry atributu může být z následujících typů:

- **bool**

- **Char**, **unsigned char**

- **krátký**, **unsigned short**

- **int**, **int bez znaménka**

- **dlouhé**, **unsigned long**

- **__int64**, **unsigned __int64**

- **float**, **double**

- **wchar_t**

- `char*` nebo `wchar_t*` nebo `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Při zadávání atributy, musí předcházet všechny nepojmenované argumenty (poziční) všechny pojmenované argumenty.

### <a name="code"></a>Kód

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Parametry atributu může být jednorozměrné pole předchozí typů.

### <a name="code"></a>Kód

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>Viz také:

[Uživatelsky definované atributy](user-defined-attributes-cpp-component-extensions.md)