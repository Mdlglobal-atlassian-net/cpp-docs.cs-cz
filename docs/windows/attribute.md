---
title: atribut | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa6c9dfa36ae753e87f0dd4b8c0fc13d3db6aeba
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679905"
---
# <a name="attribute"></a>– atribut

Umožňuje vytvořit vlastní atribut.

## <a name="syntax"></a>Syntaxe

```cpp
[ attribute(
   AllowOn,
   AllowMultiple=boolean,
   Inherited=boolean
) ]
```

### <a name="parameters"></a>Parametry

*AllowOn*  
Určuje prvky jazyka, na které můžete použít vlastní atribut. Výchozí hodnota je `System::AttributeTargets::All` (viz [System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx)).

*AllowMultiple*  
Určuje, zda vlastní atribut můžete opakovaně použít pro konstrukci. Výchozí hodnota je FALSE.

*Zděděné*  
Určuje, zda je atribut má být zděděna podtřídy. Kompilátor neposkytuje žádnou zvláštní podporu pro tuto funkci; úkolem atribut příjemců (`Reflection`, například) dodržovat tyto informace. Pokud *zděděné* má hodnotu TRUE, dědí atribut. Pokud *AllowMultiple* má hodnotu TRUE, atribut budou se hromadit na člena odvozené; Pokud *AllowMultiple* má hodnotu FALSE, atribut se přepsat (nebo nahradit) v dědičnosti. Pokud *zděděné* má hodnotu FALSE, nebude možné zdědit atribut. Výchozí hodnota je TRUE.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> **Atribut** atribut je nyní zastaralý.  Použít atribut common language runtime `System.Attribute` na přímo k vytvoření attirbutes definovaný uživatelem. Další informace najdete v tématu [uživatelem definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md).

Můžete definovat [vlastního atributu](../windows/custom-attributes-cpp.md) tak, že **atribut** atributu na definici spravované třídy nebo struktury. Název třídy je vlastní atribut. Příklad:

```cpp
[ attribute(Parameter) ]
public ref class MyAttr {};
```

definuje atribut s názvem `MyAttr` , který lze použít u funkčních parametrů. Třída musí být veřejné, pokud atribut se bude používat v jiných sestaveních.

> [!NOTE]
> Pokud chcete zabránit kolizím obor názvů, implicitně končí všechny názvy atributů s "Atribut"; v tomto příkladu je název atributu a třídy ve skutečnosti `MyAttrAttribute`, ale `MyAttr` a `MyAttrAttribute` zaměnitelné.

Veřejné konstruktory třídy definují nepojmenované parametry atributu. Přetížené konstruktory povolit více způsobů určení atributů, tak vlastní atribut, který je definován následujícím způsobem:

```cpp
// cpp_attr_ref_attribute.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes
public ref class MyAttr {
public:
   MyAttr() {}   // Constructor with no parameters
   MyAttr(int arg1) {}   // Constructor with one parameter
};

[MyAttr]
ref class ClassA {};   // Attribute with no parameters

[MyAttr(123)]
ref class ClassB {};   // Attribute with one parameter
```

Veřejné datové členy třídy a vlastnosti jsou volitelné pojmenované parametry atributu:

```cpp
// cpp_attr_ref_attribute_2.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]
ref class MyAttr {
public:
   // Property Priority becomes attribute's named parameter Priority
    property int Priority {
       void set(int value) {}
       int get() { return 0;}
   }
   // Data member Version becomes attribute's named parameter Version
   int Version;
   MyAttr() {}   // constructor with no parameters
   MyAttr(int arg1) {}   // constructor with one parameter
};

[MyAttr(123, Version=2)]
ref class ClassC {};
```

Seznam typů parametrů polí možné atributů najdete v tématu [vlastní atributy](../windows/custom-attributes-cpp.md).

Zobrazit [uživatelem definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md) diskuse o atribut cíle.

**Atribut** atribut má *AllowMultiple* parametr, který určuje, zda je vlastní atribut je jedno použití nebo multiuse (může objevit více než jednou ve stejné entity).

```cpp
// cpp_attr_ref_attribute_3.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]
ref struct MyAttr {
   MyAttr(){}
};   // MyAttr is a multiuse attribute

[MyAttr, MyAttr()]
ref class ClassA {};
```

Vlastní atribut třídy jsou odvozené přímo nebo nepřímo z <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, díky kterému budou Identifikace definice atributu v metadatech rychlé a snadné. **Atribut** atribut znamená dědičnosti z `System::Attribute`, takže není nutné explicitní odvození:

```cpp
[ attribute(Class) ]
ref class MyAttr
```

je ekvivalentem

```cpp
[ attribute(Class) ]
ref class MyAttr : System::Attribute   // OK, but redundant.
```

**atribut** je alias pro <xref:System.AttributeUsageAttribute?displayProperty=fullName> (ne atributAtribut; to je výjimka pravidlo pro pojmenování atributů).

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída ref class**, **ref struct**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_attribute_4.cpp
// compile with: /c /clr
using namespace System;
[attribute(AttributeTargets::Class)]
ref struct ABC {
   ABC(Type ^) {}
};

[ABC(String::typeid)]   // typeid operator yields System::Type ^
ref class MyClass {};
```

## <a name="example"></a>Příklad

`Inherited` Pojmenovaný argument určuje, zda se zobrazí vlastní atribut na základní třídu použita na reflexi odvozené třídy.

```cpp
// cpp_attr_ref_attribute_5.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

[attribute( AttributeTargets::Method, Inherited=false )]
ref class BaseOnlyAttribute { };

[attribute( AttributeTargets::Method, Inherited=true )]
ref class DerivedTooAttribute { };

ref struct IBase {
public:
   [BaseOnly, DerivedToo]
   virtual void meth() {}
};

// Reflection on Derived::meth will show DerivedTooAttribute
// but not BaseOnlyAttribute.
ref class Derived : public IBase {
public:
   virtual void meth() override {}
};

int main() {
   IBase ^ pIB = gcnew Derived;

   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );
   Console::WriteLine( pObjs->Length ) ;
}
```

```Output
2
```

## <a name="see-also"></a>Viz také

[Abecedně řazená referenční dokumentace k atributům](../windows/attributes-alphabetical-reference.md)  
