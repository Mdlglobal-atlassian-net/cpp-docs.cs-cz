---
title: '&lt;filesystem&gt;'
description: Popisuje třídy, funkce a typy v hlavičce filesystem standardní C++ knihovny.
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 86be11da1e2cef2fe0ca12691aeb0ce3dbe94202
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076511"
---
# &lt;filesystem&gt;

Zahrňte hlavičku &lt;filesystem> pro přístup ke třídám a funkcím, které pracují s a načítají informace o cestách, souborech a adresářích.

## <a name="syntax"></a>Syntaxe

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Ve vydané verzi sady Visual Studio 2017 nebyla hlavička \<filesystem> dosud C++ standardní. C++v rámci sady Visual Studio 2017 RTW implementuje finální koncept Standard, který najdete v [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100). Visual Studio 2017 verze 15,7 a novější podporuje nové prostředí C++ 17 \<filesystem> Standard.
> Jedná se o zcela novou implementaci, která není kompatibilní s předchozí `std::experimental` verzí. Byl nutný pro podporu symlink, opravy chyb a změny v chování vyžadovaném standardem. V současné době zahrnuje \<filesystem> k dispozici nové `std::filesystem` a předchozí `std::experimental::filesystem`. Včetně \<experimental/filesystem> poskytuje pouze starou implementaci experimental. Implementace experimental bude odebrána v další vydaných vydáních knihovny ABI.

Tato hlavička podporuje systémy souborů pro jednu ze dvou hlavních tříd hostitelských operačních systémů: Microsoft Windows a POSIX.

I když je většina funkcí společná pro oba operační systémy, tento dokument určuje, kde dochází k rozdílům. Příklad:

- Systém Windows podporuje několik kořenových názvů, například `c:` nebo `\\network_name`. Systém souborů se skládá z doménové struktury stromů, z nichž každý má vlastní kořenový adresář, jako je například `c:\` nebo `\\network_name\`, a každý s vlastním adresářem pro dokončení relativní cesty (tj. nejedná se o absolutní cestu).

- POSIX podporuje jeden strom bez názvu root, jeden kořenový adresář `/`a jeden aktuální adresář.

Dalším významným rozdílem je nativní reprezentace cest:

- Systém Windows používá sekvenci **wchar_t** zakončenou hodnotou null, která je zakódována jako UTF-16 (jeden nebo více prvků pro každý znak).

- POSIX používá sekvenci **char** zakončené znakem null, která je zakódována jako UTF-8 (jeden nebo více prvků pro každý znak).

- Objekt třídy `path` ukládá cestu v nativním formátu, ale podporuje jednoduchý převod mezi tímto uloženým formulářem a několika externími formuláři:

  - Sekvence **char** zakončená hodnotou null, která je zakódovaná jako přizpůsobená operačním systémem.

  - Sekvence **char** zakončená hodnotou null, KÓDOVANÁ jako UTF-8.

  - Sekvence **wchar_t** zakončená hodnotou null, která je zakódovaná jako přizpůsobená operačním systémem.

  - Sekvence **char16_t** zakončená hodnotou null, KÓDOVANÁ jako UTF-16.

  - Sekvence **char32_t** zakončená hodnotou null, KÓDOVANÁ jako UTF-32.

  Vzájemné převody mezi těmito reprezentacemi jsou podle potřeby využívány pomocí jedné nebo více `codecvt` omezujících vlastností. Pokud není zadán žádný konkrétní objekt národního prostředí, jsou tyto omezující vlastnosti získány z globálního národního prostředí.

Dalším rozdílem je podrobnosti, se kterými jednotlivé operační systémy umožňují zadat přístupová oprávnění k souboru nebo adresáři:

- Systém Windows zaznamenává, zda je soubor jen pro čtení, nebo zapisovatelný, atribut, který nemá žádný význam pro adresáře.

- POSIX zaznamenává, zda lze soubor číst, zapsat nebo spustit (zkontrolováno, pokud se jedná o adresář). A zda je každá operace povolená pro vlastníka, skupinu vlastníka nebo pro každého, a navíc několik dalších oprávnění.

Společné pro oba systémy jsou strukturou uloženou v cestě, jakmile se dostanete do kořenového názvu. Pro cestu `c:/abc/xyz/def.ext`:

- Kořenový název je `c:`.

- Kořenový adresář je `/`.

- Kořenová cesta je `c:/`.

- Relativní cesta je `abc/xyz/def.ext`.

- Nadřazená cesta je `c:/abc/xyz`.

- Název souboru je `def.ext`.

- Stopa je `def`.

- Rozšíření je `.ext`.

Malým rozdílem je upřednostňovaný oddělovač mezi posloupností adresářů v cestě. Oba operační systémy umožňují psát `/`lomítka, ale v některých kontextech Windows preferuje zpětné lomítko `\`. Implementace ukládá preferovaný oddělovač v datovém členu `preferred_separator` v `path`.

Nakonec `path` objekty mají důležitou funkci: můžete je použít všude, kde je vyžadován argument filename v třídách definovaných v hlavičce [\<fstream – >](fstream.md).

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Členové

### <a name="classes"></a>Třídy

|||
|-|-|
|[directory_entry – třída](../standard-library/directory-entry-class.md)|Popisuje objekt, který je vrácen `directory_iterator` nebo `recursive_directory_iterator` a obsahuje `path`.|
|[directory_iterator – třída](../standard-library/directory-iterator-class.md)|Popisuje vstupní iterátor, který sekvencí názvy souborů v adresářovém systému souborů.|
|[filesystem_error – třída](../standard-library/filesystem-error-class.md)|Základní třída pro výjimky, které jsou vyvolány pro hlášení přetečení systému nízké úrovně.|
|[path – třída](../standard-library/path-class.md)|Definuje třídu, která ukládá objekt typu šablony `String`, který je vhodný pro použití jako název souboru.|
|[recursive_directory_iterator – třída](../standard-library/recursive-directory-iterator-class.md)|Popisuje vstupní iterátor, který sekvencí názvy souborů v adresářovém systému souborů. Iterátor může také dohlížet na podadresáře.|
|[file_status – třída](../standard-library/file-status-class.md)|Zalomí `file_type`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[struktura space_info](../standard-library/space-info-structure.md)|Uchovává informace o svazku.|

## <a name="functions"></a>Functions

[\<filesystem> funkce](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operátory

[operátory \<filesystem>](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Výčty

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file](../standard-library/filesystem-functions.md#copy_file) a určuje chování, pokud cílový soubor již existuje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Výčet, který určuje možnosti pro iterátory adresáře.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Výčet pro typy souborů.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| Vytvoří výčet možností pro funkci `permissions`. |
|[oprávnění](../standard-library/filesystem-enumerations.md#perms)|Typ maskování, který slouží k předávání oprávnění a možností oprávnění|

## <a name="see-also"></a>Viz také

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
