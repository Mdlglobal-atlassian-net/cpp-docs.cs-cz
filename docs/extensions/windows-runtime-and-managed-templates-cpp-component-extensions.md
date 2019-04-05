---
title: Windows Runtime a spravované šablony (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: a8cc429763d042ba262d5543f4a2d85bbf8aa29a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029558"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime a spravované šablony (C + +/ CLI a C + +/ CX)

Šablony vám umožní definovat prototyp modulu Windows Runtime nebo společný typ modulu runtime jazyka a potom vytvořte instanci variace tohoto typu pomocí parametrů typu jinou šablonu.

## <a name="all-runtimes"></a>Všechny moduly runtime

Vytvoření šablon z typů hodnoty nebo odkazu.  Další informace o vytváření typů hodnoty nebo odkazu naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

Další informace o standardní šablony tříd C++, naleznete v tématu [šablony třídy](../cpp/class-templates.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Neexistují žádné poznámky o této funkci jazyka, které se vztahují jenom Windows Runtime.)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Existují některá omezení k vytvoření šablony třídy ze spravovaných typů, které je ukázán v následujícím příkladu kódu.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Je možné vytvořit instanci obecného typu s parametrem šablony spravovaného typu, ale nelze vytvořit instanci šablony spravované pomocí obecného typu parametru šablony. Je to proto obecné typy jsou vyřešeny za běhu. Další informace najdete v tématu [obecné typy a šablony (C + +/ CLI)](generics-and-templates-visual-cpp.md).

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

Obecný typ nebo funkce nemůže být vnořená v spravované šablony.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Nejde získat přístup šablony definovaný v odkazovaném sestavení s C + +/ syntaxi jazyka rozhraní příkazového řádku, ale můžete použít reflexe. Pokud šablona není vytvořena instance, není aktivováno v metadatech. Pokud dojde k vytvoření šablony, zobrazí se pouze odkazované členské funkce v metadatech.

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

Můžete změnit spravované Modifikátor třídy v částečné specializace nebo explicitní specializace šablony třídy.

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

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)