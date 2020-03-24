---
title: ref class a ref struct (C++/CLI a C++/CX)
ms.date: 05/30/2019
ms.topic: reference
f1_keywords:
- ref class
- value class
- ref struct
- value struct
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 78cf7cf16c4ccf29f72038fd79c5d7a1689c05ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172565"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref class a ref struct (C++/CLI a C++/CX)

Rozšíření **třídy ref class** nebo **ref struct** deklaruje třídu nebo strukturu, jejíž *životnost objektu* je spravována automaticky. Pokud objekt již není přístupný nebo je mimo rozsah, je paměť uvolněna.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="syntax"></a>Syntaxe

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};
```

### <a name="parameters"></a>Parametry

*class_access*<br/>
Volitelné Přístupnost třídy nebo struktury mimo sestavení. Možné hodnoty jsou **veřejné** a **privátní** (výchozí hodnota je**Private** ). Vnořené třídy nebo struktury nemůžou mít specifikátor *class_access* .

*Jméno*<br/>
Název třídy nebo struktury.

*upravující*<br/>
Volitelné [abstraktní](abstract-cpp-component-extensions.md) a [zapečetěné](sealed-cpp-component-extensions.md) jsou platné modifikátory.

*inherit_access*<br/>
Volitelné Přístupnost *base_type*. Jediná povolená přístupnost je **Veřejná** (**výchozí** ).

*base_type*<br/>
Volitelné Základní typ. Typ hodnoty však nemůže fungovat jako základní typ.

Další informace naleznete v části jazykově specifické popisy tohoto parametru v částech prostředí Windows Runtime a modulu CLR (Common Language Runtime).

### <a name="remarks"></a>Poznámky

Výchozí přístupnost člena objektu deklarovaného s **parametrem ref class** nebo **Value Class** je **soukromá**. A výchozí přístupnost člena objektu deklarovaného se strukturou **ref struct** nebo **value struct** je **Veřejná**.

Pokud typ odkazu dědí z jiného typu odkazu, musí být virtuální funkce v základní třídě explicitně přepsány (s [přepsáním](override-cpp-component-extensions.md)) nebo skryté (s [New (New slot v tabulce vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)). Funkce odvozené třídy musí být také explicitně označeny jako **virtuální**.

Pro detekci v době kompilace, zda je typ **ref class** nebo **ref struct**nebo **Třída hodnoty** nebo **Struktura hodnoty**, použijte `__is_ref_class (type)`, `__is_value_class (type)`nebo `__is_simple_value_class (type)`. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

Další informace o třídách a strukturách naleznete v tématu.

- [Vytváření instancí tříd a struktur](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Sémantika zásobníku C++ pro typy odkazů](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md)

- [Destruktory a finalizační metody v Postupy: definování a využívání tříd a struktur (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Uživatelem definované operátory (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Uživatelem definované převody (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Obecné třídy (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

Viz [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md) a [třídy hodnot a struktury](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="parameters"></a>Parametry

*base_type*<br/>
Volitelné Základní typ. Struktura **ref class** nebo **ref** může dědit z nula nebo více rozhraní a typu nula nebo jeden typ **ref** . Struktura **hodnot** nebo **hodnot** může dědit pouze z rozhraní nula nebo více.

Při deklaraci objektu pomocí klíčových slov **ref class** nebo **ref struct** je objekt k objektu přistupované popisovačem objektu; To znamená, že ukazatel na čítač odkazuje na objekt. Když deklarovaná proměnná přechází z oboru, kompilátor automaticky odstraní základní objekt. Když je objekt použit jako parametr ve volání nebo je uložen v proměnné, popisovač objektu je skutečně předán nebo uložen.

Při deklaraci objektu pomocí klíčových slov **třídy Value** nebo **value struct** není doba života deklarovaného objektu pod dohledem. Objekt je podobný jakékoli jiné standardní C++ třídě nebo struktuře.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny rozdíly z syntaxe uvedené v části **všechny moduly runtime** , které jsou specifické pro C++/CLI.

### <a name="parameters"></a>Parametry

*base_type*<br/>
Volitelné Základní typ. Struktura **ref class** nebo **ref** může dědit od nuly nebo více spravovaných rozhraní a nula nebo jeden typ ref. Struktura **hodnot** nebo **hodnot** může dědit pouze z nulových nebo více spravovaných rozhraní.

Klíčová slova **ref class** a **ref struct** říká kompilátoru, že třída nebo struktura má být přidělena v haldě. Když je objekt použit jako parametr ve volání nebo je uložen v proměnné, odkaz na objekt je skutečně předán nebo uložen.

Klíčová slova **Třída hodnoty** a **Struktura hodnoty** označují kompilátor, že hodnota přidělené třídy nebo struktury je předána funkcím nebo uloženým v členech.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
