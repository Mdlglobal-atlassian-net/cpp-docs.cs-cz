---
title: '&lt;systém souborů&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: 0f397d8b0c39769fde20b6aa50412c979237f70a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220371"
---
# <a name="ltfilesystemgt"></a>&lt;systém souborů&gt;

Zahrnout hlavičku &lt;filesystem > pro přístup k třídy a funkce, které pracují a načtení informací o cesty, soubory a adresáře.

## <a name="syntax"></a>Syntaxe

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Od verze Visual Studio 2017 \<systému souborů > hlavička nebyla dosud standard jazyka C++. C++v sadě Visual Studio 2017 (verze 141 MSVC) implementuje součástí standardu konečný návrh [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Tato hlavička podporuje systémy souborů z jednoho z dvě různé třídy hostitelských operačních systémech: Microsoft Windows a Posix.

Většina funkcí je společná pro obě operačních systémů, tento dokument identifikuje, kde dojde k rozdíly. Příklad:

- Windows podporuje více názvů root, například c: nebo \\\network_name. Systém souborů se skládá z doménové struktury stromů, každý s vlastní kořenový adresář, jako je například c:\ nebo \\\network_name\\a každou s vlastní aktuální adresář pro dokončení relativní cesta (jeden, který není absolutní cesta).

- POSIX podporuje jeden stromu, bez názvu kořenového jeden kořenový adresář / a jeden aktuální adresář.

Jiné podstatný rozdíl je nativní reprezentaci cest:

- Windows používá posloupnost zakončená hodnotou null wchar_t kódováním UTF-16 (jeden nebo dva prvky pro každý znak).

- POSIX využívá posloupnost zakončená hodnotou null typu char, kódováním UTF-8 (jeden nebo více prvků pro každý znak).

- Objekt třídy cesty ukládá cesty v nativním formátu, ale podporuje snadný převod mezi touto uložené formulář a externí několika způsoby:

- Posloupnost zakončená hodnotou null char zakódován jako dána podle operačního systému.

- Posloupnost zakončená hodnotou null char kódováním UTF-8.

- Posloupnost zakončená hodnotou null wchar_t zakódován jako dána podle operačního systému.

- Posloupnost zakončená hodnotou null char16_t kódováním UTF-16.

- Posloupnost zakončená hodnotou null char32_t kódováním UTF-32.

Mezi tyto reprezentace interconversions zprostředkovaného, podle potřeby pomocí jednoho nebo více `codecvt` omezujících vlastností. Pokud objekt konkrétní národní prostředí není došlo ke shodě, těchto omezujících vlastností jsou získávány z globální národní prostředí.

Další rozdíl je podrobností, které každý operační systém vám umožní určit soubor nebo adresář přístupová oprávnění:

1. Záznamy Windows určuje, zda je soubor číst pouze nebo zapisovatelný, atribut, který nemá žádný význam pro adresáře.

1. POSIX zaznamenává, jestli soubor lze číst, písemné nebo spuštěn (zkontrolovat, zda adresář), vlastník, podle vlastníka skupiny nebo podle všichni a navíc několik dalších oprávnění.

Společné pro oba systémy je struktura uložené na cestu po vyřešení název kořenového adresáře. Pro c:/abc/xyz/def.ext cesta:

- Název kořenového adresáře je c:.

- Kořenový adresář je /.

- Kořenová cesta je c: /.

- Relativní cesta je abc/xyz/def.ext.

- Cesta k nadřazenému je c:/abc/xyz.

- Název souboru je def.ext.

- Stopky je def.

- Rozšíření. externí

Malý rozdíl je **upřednostňované oddělovač**, mezi pořadí adresáře v cestě. V obou operačních systémech umožňují napsat lomítkem /, ale v některých kontextech Windows upřednostňuje zpětné lomítko \\.

Nakonec se o důležitou funkci objekty cesty je, že je můžete využít bez ohledu na to argument souboru filename je nutné v třídy definovaná v hlavičce \<fstream – >.

Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="classes"></a>Třídy

|Name|Popis|
|----------|-----------------|
|[directory_entry – třída](../standard-library/directory-entry-class.md)|Popisuje objekt, který je vrácen `directory_iterator` nebo `recursive_directory_iterator` a obsahuje cestu.|
|[directory_iterator – třída](../standard-library/directory-iterator-class.md)|Popisuje vstupní iterátor, který pořadí pomocí názvů souboru v adresáři systému souborů.|
|[filesystem_error – třída](../standard-library/filesystem-error-class.md)|Základní třída pro výjimky, které jsou vyvolány hlášení nižší úrovně systému přetečení.|
|[path – třída](../standard-library/path-class.md)|Definuje třídu, která ukládá objekt typu šablony `String` , který je vhodný pro použití jako název souboru.|
|[recursive_directory_iterator – třída](../standard-library/recursive-directory-iterator-class.md)|Popisuje vstupní iterátor, který pořadí pomocí názvů souboru v adresáři systému souborů. Iterátor může také sestup do podadresáře.|
|[file_status – třída](../standard-library/file-status-class.md)|Zabalí `file_type`.|

## <a name="structs"></a>Struktury

|Name|Popis|
|----------|-----------------|
|[space_info – struktura](../standard-library/space-info-structure.md)|Obsahuje informace o svazku.|

## <a name="functions"></a>Funkce

[\<FileSystem > funkce](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operátory

[\<FileSystem > operátory](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Výčty

|Name|Popis|
|----------|-----------------|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file –](../standard-library/filesystem-functions.md#copy_file) a určuje chování, pokud cílový soubor už existuje.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file –](../standard-library/filesystem-functions.md#copy_file) a určuje chování, pokud cílový soubor už existuje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Výčet, který určuje možnosti pro adresář iterátory.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Výčet pro typy souborů.|
|[oprávnění](../standard-library/filesystem-enumerations.md#perms)|Typ bitové masky využít k předání možnosti oprávnění a oprávnění|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
