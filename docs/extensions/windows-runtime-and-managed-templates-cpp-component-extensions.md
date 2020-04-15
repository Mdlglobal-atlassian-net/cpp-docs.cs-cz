---
title: Windows Runtime a spravované šablony (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 5765370e611e5822b3b2d156d2eee5d21e5b453d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376310"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime a spravované šablony (C++/CLI a C++/CX)

Šablony umožňují definovat prototyp typu prostředí Windows Runtime nebo common language runtime a potom vytvořit instanci variant tohoto typu pomocí různých parametrů typu šablony.

## <a name="all-runtimes"></a>Všechny moduly runtime

Šablony můžete vytvářet z typů hodnot nebo odkazů.  Další informace o vytváření typů hodnot nebo odkazů naleznete v [tématu Třídy a struktury](classes-and-structs-cpp-component-extensions.md).

Další informace o standardních šablonách tříd jazyka C++ naleznete [v tématu Šablony tříd](../cpp/class-templates.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Pro tuto jazykovou funkci nejsou k dispozici žádné poznámky, které by se vztahovaly pouze na prostředí Windows Runtime.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Existují určitá omezení pro vytváření šablon tříd ze spravovaných typů, které jsou demonstrovány v následujících příkladech kódu.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru:`/clr`

### <a name="examples"></a>Příklady

Je možné vytvořit instanci obecného typu s parametrem šablony spravovaného typu, ale nelze vytvořit instanci spravované šablony s parametrem šablony obecného typu. Důvodem je, že obecné typy jsou vyřešeny za běhu. Další informace naleznete [v tématu Obecné typy a šablony (C++/CLI)](generics-and-templates-visual-cpp.md).

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

Obecný typ nebo funkci nelze vnořit do spravované šablony.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Nelze získat přístup k šablonám definovaným v odkazovaném sestavení se syntaxí jazyka C++/CLI, ale můžete použít reflexi. Pokud šablona není vytvořena instance, není vyzařována v metadatech. Pokud je vytvořena instance šablony, zobrazí se v metadatech pouze odkazované členské funkce.

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
