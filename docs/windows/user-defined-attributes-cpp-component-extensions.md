---
title: Uživatelsky definované atributy (C + +/ CLI a C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 004c4c30c6e7e75f626e1ac87c09cb0a87f1c8cc
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328438"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Uživatelsky definované atributy (C + +/ CLI a C + +/ CX)

C + +/ CLI a C + +/ CX umožňují vytvořit atributy specifické pro platformu, které rozšiřují metadat rozhraní, třídy nebo struktury, metody, parametr nebo výčet. Tyto atributy se liší od [standardní C++ atributy](../cpp/attributes.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

Můžete použít C + +/ CX atributy vlastnosti, ale ne konstruktory a metody.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Informace a syntaxi popsanou v tomto tématu slouží k nahrazení informace uváděné v [atribut](attributes/attribute.md).

Můžete definovat vlastní atribut definování typu a provedením <xref:System.Attribute> základní třídu pro typ a volitelně použití <xref:System.AttributeUsageAttribute> atribut.

Další informace naleznete v tématu:

- [Cíle atributů](attribute-targets-cpp-component-extensions.md)

- [Typy parametrů atributů](attribute-parameter-types-cpp-component-extensions.md)

Informace o podepisování sestavení v jazyce Visual C++, naleznete v tématu [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

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

Následující příklad ukazuje některé důležité funkce vlastních atributů. Tento příklad příkladu je běžné použití vlastních atributů: vytvoření instance serveru, který může plně sama sebe popsala klientům.

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

`Object^` Typ nahrazuje neurčeného datového typu. Následující příklad definuje vlastní atribut, který přijímá pole `Object^` jako parametry.

Argumenty atributu musí být konstanty z doby kompilace; ve většině případů měly by být konstantní literály.

Zobrazit [typeid](typeid-cpp-component-extensions.md) informace o tom, jak vrátit hodnotu System::Type z bloku vlastního atributu.

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

Modul runtime vyžaduje, aby veřejnou část třídu vlastního atributu musí být serializovatelný.  Při vytváření vlastních atributů, jsou omezeny na konstanty z doby kompilace pojmenované argumenty vlastního atributu.  (Si ho představit jako posloupnost bits připojenou k rozložení třídy v metadatech.)

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