---
title: Cíle atributů (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: 8d191b284350be13111f07c4bd9d4f06ce67eb2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467701"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Cíle atributů (C + +/ CLI a C + +/ CX)

Specifikátory použití atributů umožňují zadat atribut cíle.  Každý atribut je definován použít některé prvky jazyka. Atribut může například definovat pouze pro třídy a struktury.  Následující seznam uvádí možné syntaktické prvky, na kterých je možné vlastní atribut. Kombinace těchto hodnot (pomocí logické nebo) může být použit.

Chcete-li určit atribut target, předat jeden nebo více <xref:System.AttributeTargets> enumerátory k <xref:System.AttributeUsageAttribute> při definování atributu.

Následuje seznam platné cíle atributu:

- `All` (platí pro všechny konstruktory)

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

Obvykle atribut přímo předchází prvek jazyka, ke kterému se vztahuje. V některých případech však polohu atribut nestačí k určení zamýšleného cílového atributu. Podívejte se například:

```cpp
[Attr] int MyFn(double x)...
```

Syntakticky, neexistuje žádný způsob, jak zjistit, pokud atribut má použít pro metodu nebo návratovou hodnotu metody (v takovém případě bude výchozí metodu). V takových případech lze specifikátor atributu využití. Například chcete-li atribut platí pro návratovou hodnotu, použijte `returnvalue` specifikátor následujícím způsobem:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Použití specifikátoru atributu jsou nutné v následujících situacích:

- Chcete-li určit atribut úrovně sestavení nebo modulu.

- Můžete zadat, že atribut platí pro návratovou hodnotu metody, nikoli metodu:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Můžete zadat, že atribut platí pro přistupující objekt vlastnosti, nikoli vlastnost:

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Můžete zadat, že atribut platí pro přístupový objekt události, nikoli události:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Specifikátor atributu využití platí pouze pro atribut, který následuje. To je

```cpp
[returnvalue:Attr1, Attr2]
```

se liší od

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tato ukázka předvádí, jak určit více cílů.

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

[Uživatelsky definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md)