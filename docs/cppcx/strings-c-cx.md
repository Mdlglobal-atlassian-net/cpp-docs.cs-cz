---
title: Řetězce (C + +/ CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: 8f7cbdd02cb1d38231c476ba939009a95533a046
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744310"
---
# <a name="strings-ccx"></a>Řetězce (C + +/ CX)

Představuje text v modulu Windows Runtime v jazyce C + +/ CX podle [Platform::String – třída](../cppcx/platform-string-class.md). Použití `Platform::String Class` při předání řetězce vpřed a zpět v metodách Windows Runtime tříd, nebo jsou při interakci s ostatními součástmi modulu Windows Runtime hranice binární rozhraní (ABI) aplikace. `Platform::String Class` Poskytuje metody pro několik běžných operace s řetězci, ale to není navržena jako plně funkční řetězec třídy. V modulu jazyka C++, použijte standardní řetězec typy C++ [wstring](../standard-library/basic-string-class.md) žádné významné text zpracování, a pak převod je konečný výsledek do [Platform::String ^](../cppcx/platform-string-class.md) předtím, než ji předáte do nebo z veřejné rozhraní. Je snadné a efektivní pro převod mezi `wstring` nebo `wchar_t*` a `Platform::String`.

**Fast pass**

V některých případech můžete ověřit, že můžete bezpečně sestavit kompilátor `Platform::String` nebo předat `String` na funkci bez kopírování podkladová data řetězce. Tyto operace jsou označovány jako *fast pass* a k nim dojde transparentně.

## <a name="string-construction"></a>Vytváření řetězce

Hodnota `String` objektu je neměnný (jen pro čtení) posloupnost `char16` (16-bit Unicode) znaků. Protože `String` objektu je neměnný, přiřazení nové řetězcového literálu na `String` proměnné ve skutečnosti nahradí původní `String` objektu s novou `String` objektu. Operace sřetězení zahrnují zničení původního `String` objektu a vytvoření nového objektu.

**Literály**

A *literální znak* je znak, který je uzavřen do jednoduchých uvozovek a *řetězcového literálu* je posloupnost znaků, který je uzavřen do dvojitých uvozovek. Je-li použít literál k inicializaci řetězec ^ proměnné, kompilátor předpokládá, že je literál skládá `char16` znaků. To znamená, nemusíte předcházet literál s modifikátorem řetězec "L", nebo zadejte literál ve **_T()** nebo **TEXT()** – makro. Další informace o podpoře jazyka C++ pro kódování Unicode naleznete v tématu [souhrn programování s kódem Unicode](../text/unicode-programming-summary.md).

Následující příklad ukazuje různé způsoby, jak vytvořit `String` objekty.

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Operace zpracování řetězců

`String` Třída poskytuje metody a operátory pro zřetězení, porovnání řetězců a další základní operace s řetězci. Rozsáhlejší manipulace s řetězci, použijte `String::Data()` členské funkce k načtení hodnoty `String^` objektu jako `const wchar_t*`. Potom tuto hodnotu použít k inicializaci `std::wstring`, která poskytuje funkce pro zpracování formátovaný řetězec.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Převod řetězců

A `Platform::String` může obsahovat pouze `char16` znaků, nebo `NULL` znak. Pokud má vaše aplikace pro práci s 8 bitů znaků, použijte [String::Data](../cppcx/platform-string-class.md#data) k extrakci textu jako `const wchar_t*`. Pak můžete použít odpovídající funkce Windows nebo funkce standardní knihovny pracovat s daty a převést jej zpět `wchar_t*` nebo [wstring](../standard-library/basic-string-class.md), který můžete použít k vytvoření nového `Platform::String`.

Následující fragment kódu ukazuje, jak převést `String^` do a z proměnné `wstring` proměnné. Další informace o zacházení s řetězci, který se používá v tomto příkladu najdete v tématu [basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Délka řetězce a vložené hodnoty NULL

[String::Length](../cppcx/platform-string-class.md#length) vrátí počet znaků v řetězci, nikoli počet bajtů. Pokud ho explicitně neurčíte při použití – sémantika zásobníku pro vytvoření řetězce se nepočítá ukončujícího znaku NULL.

A `Platform::String` může obsahovat vložené hodnoty NULL, ale pouze pokud hodnota NULL je výsledek operace zřetězení. Vložené znaky Null nejsou podporovány u řetězcových literálů.; proto nelze použít vložené znaky null způsobem, že k inicializaci `Platform::String`. Vložit hodnoty NULL v `Platform::String` jsou ignorovány, pokud řetězec se zobrazí, třeba když se přiřadí `TextBlock::Text` vlastnost. Vložené znaky Null se odeberou, když je vrácena hodnota řetězce `Data` vlastnost.

## <a name="stringreference"></a>StringReference

V některých případech kódu (a) obdrží std::wstring nebo wchar_t řetězec nebo L"" řetězec literálu a pouze předává je do jinou metodu, která přebírá řetězec ^ jako vstupní parametr. Jako původní řetězec samotné vyrovnávací paměti zůstává v platnosti a před vrácení funkce nezmění, můžete převést `wchar_t*` řetězec nebo řetězcový literál [Platform::stringreference –](../cppcx/platform-stringreference-class.md)a předejte mu, které místo `Platform::String^`. To je povoleno, protože `StringReference` má uživatelem definovaný převod na `Platform::String^`. S použitím `StringReference` vyvarujte další kopie dat řetězce. Ve smyčkách, kde je úspěšných velká čísla, řetězce nebo při předávání velmi dlouhých řetězců, které potenciálně dosáhnout významné výkonnostní zlepšení pomocí `StringReference`. Ale protože `StringReference` v podstatě vypůjčí původní vyrovnávací paměti pro řetězec, je nutné použít mimořádně pečlivě vyhnete se tak poškození paměti. By neměla předat `StringReference` na asynchronní metodu Pokud původní řetězec je zaručeno, že po návratu tato metoda bude v oboru. Řetězec ^, který je inicializován z StringReference vynutí přidělení a kopírování dat řetězců případě druhou operaci přiřazení. V takovém případě dojde ke ztrátě výhod výkonu `StringReference`.

Všimněte si, že `StringReference` je standardní typ třídy jazyka C++, ne ref class, nelze ji použít ve veřejném rozhraní referenční třídy, které definujete.

Následující příklad ukazuje způsob použití StringReference:

```
void GetDecodedStrings(std::vector<std::wstring> strings)
{
    using namespace Windows::Security::Cryptography;
    using namespace Windows::Storage::Streams;

    for (auto&& s : strings)
    {
        // Method signature is IBuffer^ CryptographicBuffer::DecodeFromBase64String (Platform::String^)
        // Call using StringReference:
        IBuffer^ buffer = CryptographicBuffer::DecodeFromBase64String(StringReference(s.c_str()));

        //...do something with buffer
    }
}
```
