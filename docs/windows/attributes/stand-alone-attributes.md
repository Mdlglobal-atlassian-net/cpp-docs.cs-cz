---
title: Samostatné atributy (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 7dd1f35add3b23dbd81e32a1600481eec79fe7d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033054"
---
# <a name="stand-alone-attributes"></a>Samostatné atributy

Samostatný atribut nepracuje se klíčové slovo C++ ale se víc na řádek kódu. Samostatný atribut příkazy vyžadují středníky na konci řádku.

## <a name="stand-alone-attribute-list"></a>Seznam atributů samostatné

|Atribut|Popis|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[vlastní](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[emitidl](emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracování, který se umístí do generovaného souboru.|
|[idl_module](idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](idl-quote.md)|Umožňuje použít IDL konstrukce, které nejsou podporovány v aktuální verzi jazyka Visual C++ a jejich předávání do souboru generovaného IDL.|
|[import](import.md)|Určuje jiný soubor .idl, .odl nebo .h obsahující definice, které se má odkazovat ze souboru hlavní IDL.|
|[importidl](importidl.md)|Vloží zadaného souboru do souboru generovaného IDL|
|[importlib](importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[include](include-cpp.md)|Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.|
|[includelib](includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[library_block](library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[module](module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[no_injected_text](no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|
|[pragma](pragma.md)|Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.|

## <a name="see-also"></a>Viz také:

[Atributy podle použití](attributes-by-usage.md)