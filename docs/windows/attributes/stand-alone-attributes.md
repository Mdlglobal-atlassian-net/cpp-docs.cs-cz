---
title: Samostatné atributy (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0df8cb1def78e3a7b564f268eb1b3b0a2069fb11
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062844"
---
# <a name="stand-alone-attributes"></a>Samostatné atributy

Samostatný atribut nepracuje se klíčové slovo C++ ale se víc na řádek kódu. Samostatný atribut příkazy vyžadují středníky na konci řádku.

## <a name="stand-alone-attribute-list"></a>Seznam atributů samostatné

|Atribut|Popis|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atribut.|
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

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)