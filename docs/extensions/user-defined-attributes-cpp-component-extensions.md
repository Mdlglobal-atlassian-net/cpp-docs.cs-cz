---
title: Uživatelsky definované atributy (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: aed36ac7fed7eb1f16f8648f7bcd7efb37f43a75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171889"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Uživatelsky definované atributy (C++/CLI a C++/CX)

C++/CLI a C++/CX umožňují vytvořit atributy specifické pro platformu, které prodlužují metadata rozhraní, třídy nebo struktury, metody, parametru nebo výčtu. Tyto atributy jsou odlišné od [standardních C++ atributů](../cpp/attributes.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Můžete použít C++atributy/CX na vlastnosti, ale ne na konstruktory nebo metody.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Informace a syntaxe prezentované v tomto tématu jsou určeny k nahrazení informací uvedených v [atributu](../windows/attributes/attribute.md).

Můžete definovat vlastní atribut definováním typu a vytvořením <xref:System.Attribute> základní třídy pro daný typ a volitelně použít atribut <xref:System.AttributeUsageAttribute>.

Další informace naleznete v tématu:

- [Cíle atributů](attribute-targets-cpp-component-extensions.md)

- [Typy parametrů atributů](attribute-parameter-types-cpp-component-extensions.md)

Informace o podepisování sestavení v vizuálu C++naleznete v tématu [sestavení se silným názvem (podepisování sestaveníC++) (/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje, jak definovat vlastní atribut.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

Následující příklad znázorňuje některé důležité funkce vlastních atributů. Například tento příklad ukazuje běžné použití vlastních atributů: vytvoření instance serveru, který může plně popsat na klienty.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

Typ `Object^` nahradí datový typ variant. Následující příklad definuje vlastní atribut, který přebírá pole `Object^` jako parametry.

Argumenty atributu musí být konstanty v čase kompilace; ve většině případů by měly být konstantní literály.

Informace o tom, jak vrátit hodnotu System:: Type z bloku vlastního atributu, naleznete v tématu [typeid](typeid-cpp-component-extensions.md) .

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

Modul runtime vyžaduje, aby veřejná část třídy vlastního atributu měla být serializovatelný.  Při vytváření vlastních atributů jsou pojmenované argumenty vlastního atributu omezeny na konstanty v čase kompilace.  (Můžete si ho představit jako posloupnost bitů, které jsou připojené k vašemu rozložení třídy v metadatech.)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
