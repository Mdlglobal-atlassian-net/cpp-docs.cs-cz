---
title: třídy ref class a struktura ref (C + +/ CLI a C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 34158b8d4ff2c052543328767ea928bbe5788ef0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786901"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>třídy ref class a struktura ref (C + +/ CLI a C + +/ CX)

**Třídy ref class** nebo **ref struct** rozšíření deklaraci třídy nebo struktury jehož *doba života objektu* je spravována automaticky. Když objekt již není dostupný nebo dostane mimo rozsah, se uvolní paměť.

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
(Volitelné) Usnadnění přístupu z dané třídy nebo struktury mimo sestavení. Možné hodnoty jsou **veřejné** a **privátní** (**privátní** je výchozí nastavení). Nemůže obsahovat vnořené třídy nebo struktury *class_access* specifikátor.

*Jméno*<br/>
Název třídy nebo struktury.

*modifier*<br/>
(Volitelné) [abstraktní](abstract-cpp-component-extensions.md) a [zapečetěné](sealed-cpp-component-extensions.md) jsou platné modifikátory.

*inherit_access*<br/>
(Volitelné) Přístupnost *base_type*. Pouze povolené přístupnost **veřejné** (**veřejné** je výchozí nastavení).

*base_type*<br/>
(Volitelné) Základní typ. Hodnotový typ však nemůže fungovat jako základního typu.

Další informace najdete v popisech specifické pro jazyk tohoto parametru v prostředí Windows Runtime a Common Language Runtime.

### <a name="remarks"></a>Poznámky

Deklarovaná přístupnost člena výchozí objekt pomocí **třídy ref class** nebo **hodnotu třídy** je **privátní**. A je deklarovaná přístupnost člena výchozí objekt pomocí **ref struct** nebo **hodnotu struktury** je **veřejné**.

Pokud je odkazový typ dědí z jiného typu odkaz, musí explicitně přepsat virtuální funkce v základní třídě (s [přepsat](override-cpp-component-extensions.md)) nebo skrytý (s [new (nový slot v tabulce vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)). Funkce odvozené třídy musí také být explicitně označeny jako **virtuální**.

K detekci v době kompilace, jestli je typ **třídy ref class** nebo **ref struct**, nebo **hodnotu třídy** nebo **hodnotu struktury**, použijte `__is_ref_class (type)`, `__is_value_class (type)`, nebo `__is_simple_value_class (type)`. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

Další informace o třídách a strukturách naleznete v tématu

- [Vytvoření instance třídy a struktury](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Sémantika zásobníku C++ pro typy odkazů](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Třídy, struktury a sjednocení](../cpp/classes-and-structs-cpp.md)

- [Destruktory a finalizační metody v tom, jak: Definice a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Uživatelem definované operátory (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Uživatelem definované převody (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Obecné třídy (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

Zobrazit [referenční třídy a struktury](../cppcx/ref-classes-and-structs-c-cx.md) a [hodnotové třídy a struktury](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Parametry

*base_type*<br/>
(Volitelné) Základní typ. A **třídy ref class** nebo **ref struct** může dědit z nuly nebo více rozhraní a nula nebo jedna **ref** typy. A **hodnotu třídy** nebo **hodnotu struktury** může dědit jedině z nuly nebo více rozhraní.

Pokud deklarujete objekt s použitím **třídy ref class** nebo **ref struct** klíčových slov, objekt přistupuje popisovač pro objekt, což znamená, čítač odkaz na ukazatel na objekt. Pokud proměnnou deklarovanou dostane mimo rozsah, kompilátor automaticky odstraní základní objekt. Když objekt se používá jako parametr ve volání nebo je uložen v proměnné, popisovač pro objekt skutečně předány nebo uložené.

Pokud deklarujete objekt s použitím **hodnotu třídy** nebo **hodnotu struktury** klíčová slova, dobu života objektu deklarovanému objektu není pod dohledem. Objekt je stejně jako všechny ostatní standardní C++ třídy nebo struktury.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny rozdíly v syntaxi uvedenou v **všechny moduly runtime** části, která jsou specifická pro C + +/ CLI.

### <a name="parameters"></a>Parametry

*base_type*<br/>
(Volitelné) Základní typ. A **třídy ref class** nebo **ref struct** může dědit od nuly nebo více spravovaných rozhraní a nula nebo jedna typech. A **hodnotu třídy** nebo **hodnotu struktury** může dědit jedině z nuly nebo více spravovaných rozhraních.

**Třídy ref class** a **ref struct** klíčová slova oznámení kompilátoru, která je třídu nebo strukturu, která bude přidělena v haldě. Když objekt se používá jako parametr ve volání nebo je uložen v proměnné, odkaz na objekt skutečně předány nebo uložené.

**Hodnotu třídy** a **hodnotu struktury** klíčová slova sděluje kompilátoru, že hodnota přidělené třídy nebo struktury je předán funkcím nebo uložené ve členech.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)