---
title: Cíle atributů (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: fe2c1d27042b51300d01ba70b951b7601d87701e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172617"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Cíle atributů (C++/CLI a C++/CX)

Specifikátory použití atributu umožňují zadat cíle atributů.  Každý atribut je definován pro použití s některými prvky jazyka. Například atribut může být definován pro použití pouze pro třídy a struktury.  Následující seznam obsahuje možné syntaktické prvky, na kterých lze použít vlastní atribut. Kombinace těchto hodnot (pomocí logického operátoru OR) lze použít.

Chcete-li určit cíl atributu, pro předání jednoho nebo více enumerátorů <xref:System.AttributeTargets> pro <xref:System.AttributeUsageAttribute> při definování atributu.

Následuje seznam platných cílů atributu:

- `All` (platí pro všechny konstrukce)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (platí pro sestavení jako celek)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (platí pro modul jako celek)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

Obvykle atribut přímo předchází jazykovému prvku, na který se vztahuje. V některých případech však není pozice atributu dostačující k určení zamýšleného cíle atributu. Vezměte v úvahu tento příklad:

```cpp
[Attr] int MyFn(double x)...
```

Syntakticky neexistuje žádný způsob, jak zjistit, zda je atribut určen pro použití pro metodu nebo návratovou hodnotu metody (v tomto případě je použita metoda). V takových případech lze použít specifikátor použití atributu. Například chcete-li, aby atribut byl použit pro návratovou hodnotu, použijte specifikátor `returnvalue` následujícím způsobem:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Specifikátory použití atributu jsou povinné v následujících situacích:

- Chcete-li určit atribut na úrovni sestavení nebo modulu.

- Chcete-li určit, že atribut platí pro návratovou hodnotu metody, nikoli metodu:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Chcete-li určit, že atribut se vztahuje na přistupující objekt vlastnosti, nikoli na vlastnost:

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Chcete-li určit, že atribut se vztahuje na přistupující objekt události, nikoli na událost:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Specifikátor použití atributu se vztahuje pouze na atribut, který jej bezprostředně následuje. To je

```cpp
[returnvalue:Attr1, Attr2]
```

se liší od

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

V této ukázce se dozvíte, jak zadat více cílů.

### <a name="code"></a>Kód

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>Viz také

[Uživatelsky definované atributy](user-defined-attributes-cpp-component-extensions.md)
