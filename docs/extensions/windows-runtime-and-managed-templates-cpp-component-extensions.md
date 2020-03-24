---
title: Prostředí Windows Runtime a spravované šablony (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: ce30133d9a2d1ce5a6e446093a617f3a108055c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171824"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Prostředí Windows Runtime a spravované šablony (C++/CLI a C++/CX)

Šablony umožňují definovat prototyp typu prostředí Windows Runtime nebo modulu CLR (Common Language Runtime) a pak vytvořit instanci variací tohoto typu pomocí různých parametrů typu šablony.

## <a name="all-runtimes"></a>Všechny moduly runtime

Můžete vytvářet šablony z typů hodnot nebo odkazů.  Další informace o vytváření hodnotových nebo referenčních typů naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

Další informace o šablonách C++ standardních tříd naleznete v tématu [šablony tříd](../cpp/class-templates.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Pro tuto funkci jazyka neexistují žádné poznámky, které platí jenom pro prostředí Windows Runtime.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Existují určitá omezení pro vytváření šablon třídy ze spravovaných typů, které jsou znázorněny v následujících příkladech kódu.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Je možné vytvořit instanci obecného typu s parametrem šablony spravovaného typu, ale nelze vytvořit instanci spravované šablony s parametrem šablony obecného typu. Důvodem je, že obecné typy jsou vyřešeny za běhu. Další informace najdete v tématu [Obecné typy a šablony (C++/CLI)](generics-and-templates-visual-cpp.md).

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Obecný typ nebo funkce nemohou být vnořeny do spravované šablony.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Nemůžete získat přístup k šablonám definovaným C++v odkazovaném sestavení pomocí jazykové syntaxe/CLI, ale můžete použít reflexi. Pokud není vytvořena instance šablony, není generována v metadatech. Pokud je vytvořena instance šablony, v metadatech se zobrazí pouze odkazované členské funkce.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Můžete změnit spravovaný modifikátor třídy v částečné specializaci nebo explicitní specializaci šablony třídy.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
