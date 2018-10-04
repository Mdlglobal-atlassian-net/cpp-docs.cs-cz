---
title: Atributy kompilátoru (C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789338"
---
# <a name="compiler-attributes"></a>Atributy kompilátoru

Atributy kompilátoru poskytují širokou škálu funkcí.

|Atribut|Popis|
|---------------|-----------------|
|[emitidl](emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracování, který se umístí do generovaného souboru.|
|[event_receiver](event-receiver.md)|Vytvoří přijímače událostí.|
|[event_source](event-source.md)|Vytvoří zdroj událostí.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[Implementuje](implements-cpp.md)|Určuje odesílajících rozhraních, které se musí být členy třídy typu IDL coclass.|
|[importidl](importidl.md)|Vloží zadaný souboru do generovaného souboru.|
|[importlib](importlib.md)|Díky typy, které již byly zkompilovány do jiné knihovny typů k dispozici pro vytváření knihovny typů.|
|[includelib –](includelib-cpp.md)|Způsobí, že soubor IDL nebo .h mají být zahrnuty v souboru generovaného IDL.|
|[library_block](library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[no_injected_text](no-injected-text.md)|Zabrání kompilátoru vkládání kódu v důsledku použití atributu.|
|[satype](satype.md)|Určuje datový typ `SAFEARRAY`.|
|[Verze](version-cpp.md)|Určuje konkrétní verzi napříč několika verzemi rozhraní nebo tříd.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)