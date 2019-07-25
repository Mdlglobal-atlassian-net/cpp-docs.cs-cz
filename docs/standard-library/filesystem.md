---
title: '&lt;systému souborů&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: 6f97ad75dcf3f01406f305b713b9d14cbe527c52
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457026"
---
# <a name="ltfilesystemgt"></a>&lt;systému souborů&gt;

Zahrňte > &lt;systému souborů hlaviček pro přístup ke třídám a funkcím, které pracují a načítají informace o cestách, souborech a adresářích.

## <a name="syntax"></a>Syntaxe

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Od verze sady Visual Studio 2017 \<dosud nebyla hlavička > systému souborů C++ standardem. C++v aplikaci Visual Studio 2017 (MSVC v141) implementuje finální koncept Standard, který se nachází v [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Tato hlavička podporuje systémy souborů pro jednu ze dvou hlavních tříd hostitelských operačních systémů: Microsoft Windows a POSIX.

I když je většina funkcí společná pro oba operační systémy, tento dokument určuje, kde dochází k rozdílům. Příklad:

- Systém Windows podporuje několik kořenových názvů, například c: \\nebo \network_name. Systém souborů se skládá z doménové struktury stromů, z nichž každý má vlastní kořenový adresář, například c:\. nebo \\\network_name\\a každý s aktuálním adresářem pro dokončení relativní cesty (jeden, který není absolutní cesta).

- POSIX podporuje jeden strom bez názvu root, jeden kořenový adresář/a jeden aktuální adresář.

Dalším významným rozdílem je nativní reprezentace cest:

- Systém Windows používá sekvenci wchar_t zakončenou hodnotou null, která je zakódována jako UTF-16 (jeden nebo dva prvky pro každý znak).

- POSIX používá sekvenci znaků zakončenou znakem null, která je zakódována jako UTF-8 (jeden nebo více prvků pro každý znak).

- Objekt cesty třídy uchovává cestu v nativním formátu, ale podporuje jednoduchý převod mezi tímto uloženým formulářem a několika externími formuláři:

- Sekvence znaku zakončeného hodnotou null, kódovaná jako příznaku pro operační systém.

- Sekvence znaků zakončená hodnotou null, kódovaná jako UTF-8.

- Sekvence wchar_t zakončená hodnotou null, která je zakódovaná pro operační systém.

- Sekvence char16_t zakončené znakem null kódovaná jako UTF-16.

- Sekvence char32_t zakončené znakem null kódovaná jako UTF-32.

Vzájemné převody mezi těmito reprezentacemi jsou podle potřeby využívány pomocí jedné nebo více `codecvt` omezujících vlastností. Pokud není určen konkrétní objekt národního prostředí, jsou tyto omezující vlastnosti získány z globálního národního prostředí.

Dalším rozdílem je podrobnosti, se kterými jednotlivé operační systémy umožňují zadat přístupová oprávnění k souboru nebo adresáři:

1. Systém Windows zaznamenává, zda je soubor jen pro čtení, nebo zapisovatelný, což je atribut, který nemá pro adresáře žádný význam.

1. POSIX zaznamenává, zda lze soubor číst, zapisovat nebo spustit (zkontrolováno v případě, že se jedná o adresář), vlastník, skupina vlastníka nebo každý, a navíc několik dalších oprávnění.

Společné pro oba systémy jsou strukturou uloženou v cestě, jakmile se dostanete do kořenového názvu. Pro cestu c:/abc/xyz/def. ext:

- Název kořenového adresáře je c:.

- Kořenový adresář je/.

- Kořenová cesta je c:/.

- Relativní cesta je abc/xyz/def. ext.

- Nadřazená cesta je c:/abc/xyz.

- Název souboru je def. ext.

- Kmen je def.

- Přípona je. ext.

Malým rozdílem je **upřednostňovaný oddělovač**mezi posloupností adresářů v cestě. Oba operační systémy umožňují napsat lomítko/, ale v některých kontextech Windows upřednostňují zpětné lomítko \\.

Nakonec důležitou funkcí objektů cesty je, že je můžete použít všude, kde je vyžadován argument filename v třídách definovaných v hlavičce \<fstream – >.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[directory_entry – třída](../standard-library/directory-entry-class.md)|Popisuje objekt, který je vrácen pomocí `directory_iterator` `recursive_directory_iterator` nebo a a obsahuje cestu.|
|[directory_iterator – třída](../standard-library/directory-iterator-class.md)|Popisuje vstupní iterátor, který sekvencí názvy souborů v adresářovém systému souborů.|
|[filesystem_error – třída](../standard-library/filesystem-error-class.md)|Základní třída pro výjimky, které jsou vyvolány pro hlášení přetečení systému nízké úrovně.|
|[path – třída](../standard-library/path-class.md)|Definuje třídu, která ukládá objekt typu `String` šablony, který je vhodný pro použití jako název souboru.|
|[recursive_directory_iterator – třída](../standard-library/recursive-directory-iterator-class.md)|Popisuje vstupní iterátor, který sekvencí názvy souborů v adresářovém systému souborů. Iterátor může také dohlížet na podadresáře.|
|[file_status – třída](../standard-library/file-status-class.md)|Zabalí a `file_type`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[space_info – struktura](../standard-library/space-info-structure.md)|Uchovává informace o svazku.|

## <a name="functions"></a>Funkce

[\<Funkce > systému souborů](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operátory

[\<operátoři > systému souborů](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Výčty

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file](../standard-library/filesystem-functions.md#copy_file) a určuje chování, pokud cílový soubor již existuje.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file](../standard-library/filesystem-functions.md#copy_file) a určuje chování, pokud cílový soubor již existuje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Výčet, který určuje možnosti pro iterátory adresáře.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Výčet pro typy souborů.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[oprávnění](../standard-library/filesystem-enumerations.md#perms)|Typ maskování, který slouží k předávání oprávnění a možností oprávnění|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
