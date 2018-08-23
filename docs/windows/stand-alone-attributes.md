---
title: Samostatné atributy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6562a1de8baa9a5805f044233b97bf8dd8840638
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613755"
---
# <a name="stand-alone-attributes"></a>Samostatné atributy
Samostatný atribut nepracuje se klíčové slovo C++ ale se víc na řádek kódu. Samostatný atribut příkazy vyžadují středníky na konci řádku.
  
|Atribut|Popis|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|Zadaný řetězec bez uvozovek znaků, vysílá do vygenerovaného souboru hlavičky.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|
|[emitidl](../windows/emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracování, který se umístí do generovaného souboru.|
|[idl_module](../windows/idl-module.md)|Určuje vstupní bod v knihovně DLL.|
|[idl_quote](../windows/idl-quote.md)|Umožňuje použít IDL konstrukce, které nejsou podporovány v aktuální verzi jazyka Visual C++ a jejich předávání do souboru generovaného IDL.|
|[import](../windows/import.md)|Určuje jiný soubor .idl, .odl nebo .h obsahující definice, které se má odkazovat ze souboru hlavní IDL.|
|[importidl](../windows/importidl.md)|Vloží zadaného souboru do souboru generovaného IDL|
|[importlib](../windows/importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[Zahrnout](../windows/include-cpp.md)|Určuje jeden nebo více souborů záhlaví mají být zahrnuty v souboru generovaného IDL.|
|[includelib –](../windows/includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[library_block](../windows/library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[Modul](../windows/module-cpp.md)|Bloku knihovny definuje v souboru IDL.|
|[no_injected_text](../windows/no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|
|[pragma](../windows/pragma.md)|Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.|
  
## <a name="see-also"></a>Viz také
 [Atributy podle použití](../windows/attributes-by-usage.md)