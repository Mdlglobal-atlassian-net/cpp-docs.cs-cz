---
title: '&lt;FileSystem&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
dev_langs:
- C++
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c85c19e4f23f7c6e9454793ac86a574614ec2fae
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847244"
---
# <a name="ltfilesystemgt"></a>&lt;Systém souborů&gt;

Zahrnout záhlaví &lt;filesystem > pro přístup k třídy a funkce, které pracují a načíst informace o cesty, souborů a adresářů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Od verze Visual Studio 2017 \<filesystem > hlavička nebyla dosud C++ standard. Visual C++ 2017 implementuje standardní konečné konceptu, které se nacházejí v [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Tuto hlavičku podporuje systémy pro jednu ze dvou tříd široké hostitele operačních systémů: Microsoft Windows a Posix.

Zatímco většina funkcí jsou společná pro oba operační systémy, tento dokument identifikuje, kde rozdíly probíhat. Příklad:

- Systém Windows podporuje více kořenové názvy, například c: nebo \\\network_name. Systému souborů se skládá z doménové struktury stromů, každý s vlastním kořenovým adresářem, například c:\ nebo \\\network_name\\a každou s vlastním aktuální adresář pro dokončení relativní název cesty (ten, který není absolutní cestu souboru).

- POSIX podporuje jediného stromu bez názvu kořenové, jeden kořenový adresář / a jeden aktuální adresář.

Jiné podstatný rozdíl je nativní reprezentace názvy cest:

- Windows používá ukončené hodnotou null posloupnost wchar_t, kódovaná jako UTF-16 (jeden nebo dva elementy pro každý znak).

- POSIX používá ukončené hodnotou null posloupnost char, kódovaná jako UTF-8 (jeden či více elementů pro každý znak).

- Objekt třídy cesty ukládá názvu cesty v nativním formátu, ale podporuje snadno převod mezi to uložené formuláře a několik externí formuláře:

- Ukončené hodnotou null pořadí char, kódovaná jako favored v operačním systému.

- Ukončené hodnotou null pořadí char, kódovaná jako UTF-8.

- Ukončené hodnotou null pořadí wchar_t, kódovaná jako favored v operačním systému.

- Posloupnost char16_t, kódovaná jako UTF-16 ukončené hodnotou null.

- Ukončené hodnotou null pořadí char32_t, kódovaná jako znakové sady UTF-32.

Mezi tyto reprezentace interconversions zprostředkovaného, podle potřeby pomocí jednoho nebo více `codecvt` omezující vlastnosti. Pokud není určen objekt konkrétním národním prostředím, tyto omezující vlastnosti jsou získávány z globální národní prostředí.

Další rozdíl je podrobnosti, pomocí kterého každý operační systém, umožní vám zadat soubor nebo adresář přístupová oprávnění:

1. Windows záznamy o tom, zda je soubor číst pouze nebo s možností zápisu, atribut, který nemá žádný význam pro adresáře.

1. POSIX zaznamenává, jestli soubor lze číst, písemné nebo spuštění (zkontrolovat, zda adresář), je vlastník, podle vlastníka skupiny nebo každý uživatel a navíc několik dalších oprávnění.

Společné pro oběma systémy je strukturu ukládat, pathname po získání za název kořenového adresáře. Pro pathname c:/abc/xyz/def.ext:

- Název kořenového je c:.

- Kořenový adresář je /.

- Kořenová cesta je c: /.

- Relativní cesta je abc/xyz/def.ext.

- Nadřazená cesta je c:/abc nebo xyz.

- Název souboru je def.ext.

- Stopky je def.

- Rozšíření. ext.

Malý rozdíl je **upřednostňované oddělovače**, mezi pořadí adresáře v cestě. Obě operačních systémů umožňují zápisu lomítkem /, ale v některých kontextech Windows upřednostní zpětné lomítko \\.

Nakonec důležitou součást objektů cesty je, že je můžete používat kdekoli v tříd definovaných v hlavičce je vyžadován název souboru by \<fstream >.

Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[directory_entry – třída](../standard-library/directory-entry-class.md)|Popisuje objekt, který je vrácen `directory_iterator` nebo `recursive_directory_iterator` a obsahuje cestu.|
|[directory_iterator – třída](../standard-library/directory-iterator-class.md)|Popisuje vstupní iterator, který pořadí prostřednictvím názvy souborů v adresáři systému souborů.|
|[filesystem_error – třída](../standard-library/filesystem-error-class.md)|Základní třída pro výjimky, které jsou vyvolány nahlásit nízké úrovně systému přetečení.|
|[path – třída](../standard-library/path-class.md)|Definuje třídu, která ukládá objekt typu šablony `String` , je vhodné použít jako název souboru.|
|[recursive_directory_iterator – třída](../standard-library/recursive-directory-iterator-class.md)|Popisuje vstupní iterator, který pořadí prostřednictvím názvy souborů v adresáři systému souborů. Iteraci můžete také sestup do podadresářů.|
|[file_status – třída](../standard-library/file-status-class.md)|Zabalí `file_type`.|

## <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[space_info – struktura](../standard-library/space-info-structure.md)|Obsahuje informace o svazku.|

## <a name="functions"></a>Funkce

[\<FileSystem > funkce](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operátory

[\<FileSystem > operátory](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Výčet, který se používá s [copy_file –](http://msdn.microsoft.com/4af7a9b0-8861-45ed-b84e-0307f0669d60) a určuje chování, pokud cílový soubor již existuje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Výčet, který určuje možnosti, iterátory adresáře.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Výčet pro typy souborů.|
|[oprávnění](../standard-library/filesystem-enumerations.md#perms)|Typ bitová maska používá k předání informací o tom oprávnění a možnosti pro oprávnění|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
