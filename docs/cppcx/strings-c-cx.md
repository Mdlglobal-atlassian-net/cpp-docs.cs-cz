---
title: Řetězce (C++/CX)
ms.date: 01/22/2017
ms.assetid: 5b34e1df-7c2b-4269-aba8-b767d36c49d9
ms.openlocfilehash: a67b9a4552dc83791c05029cca76f60fd83df0f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745338"
---
# <a name="strings-ccx"></a>Řetězce (C++/CX)

Text v prostředí Windows Runtime je v jazyce C++/CX reprezentován [třídou Platform::String .](../cppcx/platform-string-class.md) `Platform::String Class` Při předávání řetězců tam a zpět metodám ve třídách prostředí Windows Runtime nebo při interakci s jinými součástmi prostředí Windows Runtime přes hranici binárního rozhraní aplikace (ABI). Poskytuje `Platform::String Class` metody pro několik běžných operací řetězce, ale není navržen tak, aby se plně vybavený řetězec třídy. V modulu Jazyka C++ použijte standardní typy řetězců jazyka C++, jako je [wstring](../standard-library/basic-string-class.md) pro jakékoli významné zpracování textu, a potom převeďte konečný výsledek na [Platform::String^](../cppcx/platform-string-class.md) před předáním do nebo z veřejného rozhraní. Je to snadné a efektivní `wstring` `wchar_t*` převést mezi nebo a `Platform::String`.

**Rychlý průchod**

V některých případech kompilátor můžete ověřit, `Platform::String` že `String` může bezpečně sestavit nebo předat funkci bez kopírování podkladových řetězcových dat. Tyto operace jsou označovány jako *rychlý průchod* a dochází transparentně.

## <a name="string-construction"></a>Konstrukce strun

Hodnota objektu `String` je neměnná (jen pro čtení) sekvence `char16` (16bitové znaky Unicode). Vzhledem `String` k tomu, že objekt je neměnný, přiřazení literálu nového řetězce k `String` proměnné ve skutečnosti nahradí původní `String` objekt novým `String` objektem. Operace zřetězení zahrnují zničení `String` původního objektu a vytvoření nového objektu.

**Literály**

Znak *literálu* je znak, který je uzavřen v jednoduchých uvozovkách a *literál řetězec* je posloupnost znaků, která je uzavřena v uvozovkách. Pokud použijete literál k inicializaci string^ proměnné, kompilátor předpokládá, že literál se skládá ze `char16` znaků. To znamená, že není třeba předcházet literálu s modifikátorem řetězce L nebo uzavřete literál v makru **_T()** nebo **TEXT().** Další informace o podpoře jazyka C++ pro kódování Unicode naleznete v [tématu Unicode Programming Summary](../text/unicode-programming-summary.md).

Následující příklad ukazuje různé `String` způsoby vytváření objektů.

[!code-cpp[cx_strings#01](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#01)]

## <a name="string-handling-operations"></a>Operace zpracování řetězců

Třída `String` poskytuje metody a operátory pro zřetězení, porovnání řetězců a další základní operace řetězce. Chcete-li provést rozsáhlejší manipulace `String::Data()` s řetězci, použijte `String^` členovou `const wchar_t*`funkci k načtení hodnoty objektu jako . Pak použijte tuto hodnotu `std::wstring`k inicializaci , který poskytuje bohaté funkce zpracování řetězce.

[!code-cpp[cx_strings#03](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#03)]

## <a name="string-conversions"></a>Převody řetězců

A `Platform::String` může `char16` obsahovat pouze `NULL` znaky nebo znak. Pokud vaše aplikace má pracovat s 8bitové znaky, použijte [String::Data](../cppcx/platform-string-class.md#data) extrahovat text jako `const wchar_t*`. Potom můžete použít příslušné funkce systému Windows nebo standardní knihovny pracovat `wchar_t*` s daty a převést zpět `Platform::String`na nebo [wstring](../standard-library/basic-string-class.md), které můžete použít k vytvoření nového .

Následující fragment kódu ukazuje, `String^` jak převést `wstring` proměnnou do a z proměnné. Další informace o manipulaci s řetězci, která se používá v tomto příkladu, naleznete [v tématu basic_string::replace](../standard-library/basic-string-class.md#replace).

[!code-cpp[cx_strings#04](../cppcx/codesnippet/CPP/cppcx_strings/class1.cpp#04)]

## <a name="string-length-and-embedded-null-values"></a>Délka řetězce a vložené hodnoty NULL

[Funkce String::Length](../cppcx/platform-string-class.md#length) vrátí počet znaků v řetězci, nikoli počet bajtů. Ukončující znak NULL se nepočítá, pokud jej explicitně neurčíte při použití sémantiky zásobníku k vytvoření řetězce.

A `Platform::String` může obsahovat vložené hodnoty NULL, ale pouze v případě, že null je výsledkem operace zřetězení. Vložené null nejsou podporovány v řetězcových literále; Proto nelze použít vložené nulls tímto způsobem `Platform::String`k inicializaci . Vložené hodnoty NULL `Platform::String` v a jsou ignorovány při zobrazení řetězce, například `TextBlock::Text` když je přiřazen k vlastnosti. Vložené nulls jsou odebrány při hodnota `Data` řetězce je vrácena vlastností.

## <a name="stringreference"></a>Odkaz na řetězec

V některých případech váš kód (a) obdrží std::wstring, nebo wchar_t řetězci nebo L"" řetězci literálu a jen předává ji na jinou metodu, která trvá String^ jako vstupní parametr. Dokud původní vyrovnávací paměť řetězce zůstane platná a nezmutuje před `wchar_t*` návratem funkce, můžete převést literál řetězce nebo řetězce `Platform::String^`na [platformu::StringReference](../cppcx/platform-stringreference-class.md)a předat ji místo . To je `StringReference` povoleno, protože má `Platform::String^`uživatelem definovaný převod na . Pomocí `StringReference` můžete vyhnout vytváření další kopii dat řetězce. Ve smyčkách, kde předáváte velký počet řetězců nebo při předávání velmi velkých řetězců, `StringReference`můžete potenciálně dosáhnout významného zlepšení výkonu pomocí . Ale `StringReference` protože v podstatě vypůjčí původní vyrovnávací paměti řetězce, je nutné použít extrémní péči, aby se zabránilo poškození paměti. Neměli byste `StringReference` předat asynchronní metodu, pokud původní řetězec je zaručeno, že bude v oboru, když tato metoda vrátí. Řetězec^, který je inicializován z StringReference vynutí přidělení a kopii dat řetězce, pokud dojde k druhé operaci přiřazení. V takovém případě ztratíte výhodu výkonu `StringReference`.

Všimněte `StringReference` si, že je standardní c++ typ třídy, nikoli ref třídy, nelze použít ve veřejném rozhraní ref třídy, které definujete.

Následující příklad ukazuje, jak používat StringReference:

```cpp
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
