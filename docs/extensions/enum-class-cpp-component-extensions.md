---
title: Enum – třídaC++(/CLI C++a/CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: 6305d41febfe4d55b2b84062e76ff62c3ea2b18a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182133"
---
# <a name="enum-class--ccli-and-ccx"></a>Enum – třídaC++(/CLI C++a/CX)

Deklaruje výčet v oboru názvů, což je uživatelsky definovaný typ tvořený sadou pojmenovaných konstant nazývaných enumerátory.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="remarks"></a>Poznámky

C++/CX a C++/CLI podporují **veřejnou třídu enum** a **soukromou třídu enum** , která je podobná C++ standardní **třídě výčtu** , ale s přičtením specifikátoru přístupnosti. V rámci **/CLR**je povolen typ **třídy výčtu** c++ 11, ale generuje upozornění C4472, které má být zajištěno, že skutečně POŽADUJEte typ výčtu ISO, a ne C++typ/CX C++a/CLI. Další informace o klíčovém slově C++ standard **Enum** ISO naleznete v tématu [výčty](../cpp/enumerations-cpp.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="syntax"></a>Syntaxe

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>Parametry

*stoupit*<br/>
Přístupnost výčtu, který může být **veřejný** nebo **soukromý**.

*identifikátor výčtu*<br/>
Název výčtu.

*základní typ*<br/>
Volitelné Základní typ výčtu.

Volitelné. Pouze prostředí Windows Runtime) nadřízený typ výčtu, což může být **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64`nebo `uint64`.

*enumerátor – seznam*<br/>
Seznam názvů enumerátorů oddělených čárkami.

Hodnota každého enumerátoru je konstantní výraz, který je buď definován implicitně kompilátorem, nebo explicitně zápisem, *enumerátor*`=`*konstantní výraz*. Ve výchozím nastavení je hodnota prvního enumerátoru nula, pokud je implicitně definován. Hodnota každého následného implicitně definovaného enumerátoru je hodnota předchozího výčtu + 1.

*var*<br/>
Volitelné Název proměnné typu výčtu.

### <a name="remarks"></a>Poznámky

Další informace a příklady naleznete v tématu [výčty](../cppcx/enums-c-cx.md).

Všimněte si, že kompilátor generuje chybové zprávy, pokud konstantní výraz definující hodnotu výčtu nemůže být reprezentovaný *podkladovým typem*.  Kompilátor však nehlásí chybu pro hodnotu, která není pro podkladový typ vhodná. Příklad:

- Pokud je *základní typ* numerický a enumerátor určuje maximální hodnotu pro tento typ, hodnota další implicitně definovaného enumeratoin nemůže být reprezentovaná.

- Pokud je *základní typ* **logická**hodnota a více než dva enumerátory jsou implicitně definovány, enumerátory po prvních dvou nelze reprezentovat.

- Pokud je *základní typ* `char16`a rozsah hodnoty výčtu z 0XD800 až 0xDFFF, může být hodnota reprezentovaná. Hodnota je ale logicky nesprávná, protože představuje poloviční dvojici Unicode a neměla by se zobrazovat v izolaci.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parametry

*stoupit*<br/>
Přístupnost výčtu. Může být buď **Veřejná** , nebo **soukromá**.

*enumerátor – seznam*<br/>
Čárkami oddělený seznam identifikátorů (výčty) ve výčtu.

*Jméno*<br/>
Název výčtu. Anonymní spravované výčty nejsou povolené.

*type*<br/>
Volitelné Základní typ *identifikátorů*. Může to být jakýkoli skalární typ, například podepsaná nebo nepodepsaná verze **int**, **short**nebo **Long**.  také je povolena **logická** hodnota nebo **znak** .

*var*<br/>
Volitelné Název proměnné typu výčtu.

### <a name="remarks"></a>Poznámky

**enum class** a **Enum struct** jsou ekvivalentní deklarace.

Existují dva typy výčtů: spravované nebo C++/CX a Standard.

Spravovaný nebo C++/CX enum může být definován následujícím způsobem:

```cpp
public enum class day {sun, mon };
```

a je sémanticky ekvivalentní:

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Standardní výčet může být definován následujícím způsobem:

```cpp
enum day2 { sun, mon };
```

a je sémanticky ekvivalentní:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Spravované názvy enumerátorů (*identifikátory*) nejsou vloženy do oboru, ve kterém je definován výčet; všechny odkazy na enumerátory musí být plně kvalifikované (*název*`::`*identifikátor*).  Z tohoto důvodu nemůžete definovat anonymní spravovaný výčet.

Enumerátory standardního výčtu jsou silně vloženy do ohraničujícího oboru.  To znamená, že pokud je v ohraničujícím oboru k dispozici jiný symbol se stejným názvem jako enumerátor, kompilátor vygeneruje chybu.

V aplikaci Visual Studio 2002 a Visual Studio 2003 byly výčty slabě vloženy (viditelné v nadřazeném oboru, pokud neexistuje jiný identifikátor se stejným názvem).

Pokud je definován C++ standardní výčet (bez **třídy** nebo **struktury**), kompilování s `/clr` způsobí, že se výčet zkompiluje jako spravovaný výčet.  Výčet stále obsahuje sémantiku nespravovaného výčtu.  Všimněte si, že kompilátor vloží atribut, `Microsoft::VisualC::NativeEnumAttribute` pro identifikaci záměru programátora pro výčet jako nativní výčet.  Další kompilátory jednoduše uvidí standardní výčet jako spravovaný výčet.

Pojmenovaný standardní výčet kompilovaný s `/clr` bude v sestavení viditelný jako spravovaný výčet a může být zpracován jakýmkoli jiným spravovaným kompilátorem.   Nejmenovaný standardní výčet ale nebude veřejně viditelný ze sestavení.

V aplikaci Visual Studio 2002 a Visual Studio 2003 byl standardní výčet použit jako typ v parametru funkce:

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

vygeneruje následující kód v jazyce MSIL pro podpis funkce:

```cpp
void f(int32);
```

V aktuálních verzích kompilátoru se však standardní výčet generuje jako spravovaný výčet s [NativeEnumAttribute] a v jazyce MSIL pro podpis funkce:

```cpp
void f(E)
```

Další informace o nativních výčtech naleznete v tématu [ C++ deklarace výčtu](../cpp/enumerations-cpp.md).

Další informace o výčtech CLR naleznete v tématu:

- [Nadřízený typ výčtu](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
