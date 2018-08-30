---
title: enum class (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 625b99751c570c47456aad4903de5b8c4049ac42
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207599"
---
# <a name="enum-class--c-component-extensions"></a>enum class (rozšíření komponent C++)

Deklaruje výčet v oboru názvů, který je uživatelem definovaný typ tvořený sadou pojmenovaných konstant nazývaných enumerátory.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="remarks"></a>Poznámky

C + +/ CX a C + +/ podpora rozhraní příkazového řádku **veřejný výčet tříd** a **soukromý výčet tříd** které jsou podobně jako standardní C++ **výčet tříd** , ale s přidáním usnadnění přístupu specifikátor. V části **/CLR**, C ++ 11 **výčet tříd** typ je povolené, ale bude generovat upozornění C4472, která je určena k zajištění, že Opravdu chcete typ výčtu ISO a není jazyce C + +/ CX a C + +/ CLI typu. Další informace o standardu ISO C++ **výčtu** – klíčové slovo, naleznete v tématu [výčty](../cpp/enumerations-cpp.md).

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

*Přístup*  
Usnadnění výčet, který může být **veřejné** nebo **privátní**.

*Identifikátor výčtu*  
Název výčtu.

*Základní typ*  
(Volitelné) Základní typ výčtu.

(Volitelné. Pouze Windows Runtime) základní typ výčtu, který může být **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64`, nebo `uint64`.

*seznam výčtu*  
Čárkami oddělený seznam názvů enumerátor.

Hodnota každého výčtu je konstantní výraz, který je buď definován implicitně kompilátorem, nebo explicitně zápisu, *enumerátor*`=`*konstantní výraz*. Ve výchozím nastavení hodnota první čítače výčtu je nula, pokud je implicitně definovaný. Hodnotu každé následné implicitně definovaný enumerátor je hodnota z předchozího výčtu + 1.

*var*  
(Volitelné) Název proměnné typu výčtu.

### <a name="remarks"></a>Poznámky

Další informace a příklady najdete v tématu [výčty](https://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).

Všimněte si, že kompilátor vydá chybové zprávy, pokud nemůže být reprezentována konstantní výraz, který definuje hodnotu čítače *základní typ*.  Kompilátor nehlásí chybu, která je nevhodná pro základní typ hodnoty. Příklad:

- Pokud *základní typ* jsou číselná a enumerátor určuje maximální hodnotu pro daný typ, hodnotu Další implicitně definovaný enumeratoin nejde reprezentovat.

- Pokud *základní typ* je **bool**, a více než dva čítače jsou implicitně definovaný, enumerátory po první dva nemůže být reprezentovaný.

- Pokud *základní typ* je `char16`a hodnota výčtu rozsahu 0xD800 až 0xDFFF, může být reprezentována hodnotu. Však hodnotu logicky nesprávná, protože představuje poloviční Unicode náhradní pár a neměla by se zobrazit v izolaci.

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parametry

*Přístup*  
Přístupnost člena výčtu. Může být buď **veřejné** nebo **privátní**.

*seznam výčtu*  
Čárkou oddělený seznam identifikátorů (enumerátory) ve výčtu.

*Jméno*  
Název výčtu. Anonymní výčty spravované nejsou povoleny.

*typ* (volitelné)  
Základní typ *identifikátory*. To může být libovolného skalárního typu, jako je například podepsaná nebo nepodepsaná verze z **int**, **krátký**, nebo **dlouhé**.  **BOOL** nebo **char** je také povolena.

*var* (volitelné)  
Název proměnné typu výčtu.

### <a name="remarks"></a>Poznámky

**Třída výčtu** a **enum struct** jsou ekvivalentní deklarace.

Existují dva typy výčtů: spravované nebo C + +/ CX a standard.

Spravované nebo C + +/ CX výčtu může být definovaná následujícím způsobem

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

Standardní výčtu může být definovaná následujícím způsobem:

```cpp
enum day2 { sun, mon };
```

a je sémanticky ekvivalentní:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Spravované názvy výčtů (*identifikátory*) se vloží do rozsahu, kde je definován výčet; všechny odkazy na čítačů musí být plně kvalifikovanou (*název* `::` *identifikátor*).  Z tohoto důvodu nejde definovat anonymní spravovaného výčtu.

Enumerátory standardní výčtu jsou silně vloženy do nadřazeného oboru.  To znamená pokud existuje další symbol se stejným názvem jako enumerátor v nadřazeném oboru, kompilátor vygeneruje chybu.

Ve Visual C++ 2002 a Visual C++ 2003 bylo vložený enumerátory slabě (viditelná v ohraničujícím oboru Pokud byl jiný identifikátor se stejným názvem).

Pokud je definován standardní výčtu C++ (bez **třídy** nebo **struktura**), kompilace s `/clr` způsobí, že výčet se zkompiluje jako spravovaného výčtu.  Výčet má stále sémantiku Nespravovaný výčet.  Mějte na paměti, kompilátor vkládá atribut `Microsoft::VisualC::NativeEnumAttribute`, které kompilátor Visual C++ rozpoznává k identifikaci záměr programátora ve výčtu být nativní výčet.  Jiné kompilátory jednoduše zobrazí standardní výčtu jako spravovaného výčtu.

Objekt s názvem, zkompilovaná standardní výčtu `/clr` se nebude zobrazovat v sestavení spravovaného výčtu a můžou je využívat jiné spravované kompilátoru.   Nepojmenované standardní výčet však nebudou veřejně viditelné ze sestavení.

V aplikaci Visual C++ 2002 a Visual C++ 2003, standard výčtu použít jako typ parametru funkce:

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

bude generovat následující do jazyka MSIL pro podpis funkce:

```cpp
void f(int32);
```

V aktuální verze kompilátoru, ale je standardní výčtu generované jako spravovaného výčtu s [NativeEnumAttribute] a následující podpis funkce v jazyce MSIL:

```cpp
void f(E)  
```

Další informace o nativních výčtech naleznete v tématu [deklarace výčtu v jazyce C++](../cpp/enumerations-cpp.md).

Další informace o výčtech CLR naleznete v tématu:

- [Nadřízený typ výčtu](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

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

[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)