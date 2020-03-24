---
title: Pole (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: ecd8425bf7bcc9772d7b1327add79b89aea629a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182237"
---
# <a name="arrays-ccli-and-ccx"></a>Pole (C++/CLI a C++/CX)

Typ `Platform::Array<T>` v C++/CX nebo klíčové slovo **Array** v C++/CLI deklaruje pole zadaného typu a počáteční hodnotu.

## <a name="all-platforms"></a>Všechny platformy

Pole musí být deklarováno pomocí modifikátoru Handle-to-Object (^) za pravou ostrou závorku (>) v deklaraci.
Počet elementů pole není součástí typu. Jedna proměnná pole může odkazovat na pole různých velikostí.

Na rozdíl od C++Standard, nelze podscriptovat synonymum pro aritmetický ukazatel a není komutativní.

Další informace o polích naleznete v tématu:

- [Postupy: Používání polí v jazyce C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Seznamy argumentů s proměnnou délkou (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>prostředí Windows Runtime

Pole jsou členy `Platform` oboru názvů. Pole mohou být pouze jednorozměrné.

### <a name="syntax"></a>Syntaxe

První příklad syntaxe používá klíčové slovo **New** Aggregate k přidělení pole. Druhý příklad deklaruje místní pole.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*kvalifikátory*<br/>
Volitelné Jeden nebo více těchto specifikátorů třídy úložiště: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*Typ pole*<br/>
Typ proměnné pole Platné typy jsou prostředí Windows Runtime třídy a základní typy, referenční třídy a struktury, třídy hodnot a struktury a nativní ukazatele (`type*`).

*pořadí*<br/>
Volitelné Počet rozměrů pole. Musí být 1.

*RID*<br/>
Název proměnné pole

*typ inicializace*<br/>
Typ hodnot, které inicializují pole. Typ *pole* a *typ inicializace* je typicky stejný typ. Typy však mohou být rozdílné, pokud existuje převod *typu inicializace* na *Typ pole*– například pokud je *typ inicializace* odvozen z *typu Array*.

*seznam inicializace*<br/>
Volitelné Seznam hodnot oddělených čárkami ve složených závorkách, které inicializují prvky pole. Například pokud `(3)`*Rank-Size-list* , který deklaruje jednorozměrné pole 3 prvky, *inicializační seznam* by mohl být `{1,2,3}`.

### <a name="remarks"></a>Poznámky

Můžete detekovat v době kompilace, zda je typ pole s vypočítanými odkazy s `__is_ref_array(type)`. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

### <a name="examples"></a>Příklady

Následující příklad vytvoří jednorozměrné pole, které má prvky 100.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="syntax"></a>Syntaxe

První příklad syntaxe používá klíčové slovo **gcnew** k přidělení pole. Druhý příklad deklaruje místní pole.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*kvalifikátory*<br/>
Volitelné Jeden nebo více těchto specifikátorů třídy úložiště: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/using-extern-to-specify-linkage.md), [static](../cpp/static-members-cpp.md).

*Typ pole*<br/>
Typ proměnné pole Platné typy jsou prostředí Windows Runtime tříd a základních typů, referenčních tříd a struktur, tříd hodnot a struktur, nativních ukazatelů (`type*`) a nativních typů POD (prostých starých dat).

*pořadí*<br/>
Volitelné Počet rozměrů pole. Výchozí hodnota je 1; maximální hodnota je 32. Každá dimenze pole je sama o Array.

*RID*<br/>
Název proměnné pole

*typ inicializace*<br/>
Typ hodnot, které inicializují pole. Typ *pole* a *typ inicializace* je typicky stejný typ. Typy však mohou být rozdílné, pokud existuje převod *typu inicializace* na *Typ pole*– například pokud je *typ inicializace* odvozen z *typu Array*.

*Rank-Size-list*<br/>
Seznam velikosti každé dimenze v poli oddělený čárkami. Případně, pokud je zadán parametr *inicializačního seznamu* , kompilátor může odvodit velikost každé dimenze a *seznam rozsah-velikost-seznam* může být vynechán.

*seznam inicializace*<br/>
Volitelné Seznam hodnot oddělených čárkami ve složených závorkách, které inicializují prvky pole. Nebo čárkami oddělený seznam položek vnořených *inicializačních seznamů* , které inicializují prvky v multidimenzionálním poli.

Například pokud `(3)`*Rank-Size-list* , který deklaruje jednorozměrné pole 3 prvky, *inicializační seznam* by mohl být `{1,2,3}`. Pokud byly `(3,2,4)`*Rank-Size-list* , který deklaruje trojrozměrné pole 3 elementy v prvním rozměru, 2 elementy v druhém a 4 elementy ve třetí, *inicializační seznam* by mohl být `{{1,2,3},{0,0},{-5,10,-21,99}}`.)

### <a name="remarks"></a>Poznámky

**pole** je v oboru názvů [Platform, default a CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Podobně jako C++Standard, indexy pole jsou počítány od nuly a pole je v dolním indexu pomocí hranatých závorek ([]). Na rozdíl od C++standardu jsou indexy multidimenzionálního pole uvedeny v seznamu indexů pro každou dimenzi místo sady operátorů hranatých závorek ([]) pro každou dimenzi. Například *identifikátor*[*index1*, *index2*] namísto *identifikátoru*[*index1*] [ *index2*].

Všechna spravovaná pole dědí z `System::Array`. Jakoukoli metodu nebo vlastnost `System::Array` lze použít přímo na proměnnou pole.

Pokud přidělíte pole, jehož typ elementu je ukazatel na spravovanou třídu, prvky jsou inicializovány 0.

Při přidělení pole, jehož typ elementu je typ hodnoty `V`, je výchozí konstruktor pro `V` použit pro každý prvek pole. Další informace naleznete v tématu [.NET Framework ekvivalenty C++ nativních typů (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md).

V době kompilace můžete zjistit, zda je typ pole modulu CLR (Common Language Runtime) s `__is_ref_array(type)`. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad vytvoří jednorozměrné pole, které má prvky 100, a trojrozměrné pole, které má 3 elementy v prvním rozměru, 5 prvků v druhém a 6 elementy třetí.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
