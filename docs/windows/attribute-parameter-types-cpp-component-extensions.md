---
title: Atribut parametru typy (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84c97dc0eb449ed0a2e835c46e77981dda0b67e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611903"
---
# <a name="attribute-parameter-types--c-component-extensions"></a>Typy parametrů atributů (rozšíření komponent C++)

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

## <a name="see-also"></a>Viz také

[Uživatelsky definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md)