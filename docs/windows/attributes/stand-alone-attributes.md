---
title: Samostatné atributy (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166166"
---
# <a name="stand-alone-attributes"></a>Samostatné atributy

Samostatný atribut nepracuje na C++ klíčovém slově, ale je více podobný jako řádek kódu. Samostatné příkazy atributů vyžadují středník na konci řádku.

## <a name="stand-alone-attribute-list"></a>Seznam samostatných atributů

|Atribut|Popis|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Vygeneruje zadaný řetězec bez znaků uvozovky do vygenerovaného souboru hlaviček.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](db-command.md)|Vytvoří příkaz OLE DB.|
|[emitidl](emitidl.md)|Určuje, zda budou všechny následné atributy IDL zpracovány a umístěny do generovaného souboru IDL.|
|[idl_module](idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](idl-quote.md)|Umožňuje použít konstrukce IDL, které nejsou podporovány v aktuální verzi vizuálu C++ a předávat je do generovaného souboru. idl.|
|[import](import.md)|Určuje jiný soubor. idl,. odl nebo. h obsahující definice, na které chcete odkazovat z hlavního souboru. idl.|
|[importidl](importidl.md)|Vloží zadaný soubor. idl do vygenerovaného souboru IDL.|
|[importlib](importlib.md)|Vytvoří typy, které již byly zkompilovány do jiné knihovny typů, které jsou k dispozici pro vytvoření knihovny typů.|
|[include](include-cpp.md)|Určuje jeden nebo více hlavičkových souborů, které mají být zahrnuty do vygenerovaného souboru IDL.|
|[includelib](includelib-cpp.md)|Způsobí, že soubor. idl nebo. h bude zahrnut do generovaného souboru IDL.|
|[library_block](library-block.md)|Umístí konstrukci do bloku knihovny souboru. idl.|
|[module](module-cpp.md)|Definuje blok knihovny v souboru. idl.|
|[no_injected_text](no-injected-text.md)|Zabraňuje kompilátoru v vkládání kódu v důsledku použití atributu.|
|[pragma](pragma.md)|Vygeneruje zadaný řetězec bez znaků uvozovky do generovaného souboru. idl.|

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)
