---
title: Základní mechanismy atributů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], inserting in code
- attributes [C++/CLI], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f6563d61988beb5df91ce0a3ccb871e3a5a9adc
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315940"
---
# <a name="basic-mechanics-of-attributes"></a>Základní mechanismy atributů

Existují tři způsoby, jak vložit atributy do projektu. Nejprve můžete je ručně do zdrojového kódu. Za druhé můžete vložit pomocí mřížky vlastností objektu ve vašem projektu. Nakonec můžete vložit pomocí různých průvodců. Další informace o používání **vlastnosti** okno a různých průvodců, najdete v části [vytváření a správa projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).

Jako dříve, při sestavení projektu, kompilátor analyzuje každý zdrojový soubor jazyka C++, vytváření soubor objektu. Ale když kompilátor narazí atribut, je analyzovat a syntakticky ověřit. Kompilátor poté zavolá dynamicky poskytovatele atributu vložení kódu a provádět další úpravy v době kompilace. Implementace zprostředkovatele se liší v závislosti na typu atributu. Například Atlprov.dll implementují související ATL atributy.

Následující obrázek ukazuje vztah mezi kompilátoru a poskytovatele atributu.

![Atribut komunikace komponent](../windows/media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> Použití atributu nezmění obsah zdrojového souboru. Kód vygenerovaný atributu je viditelné se pouze během relace ladění. Kromě toho pro každý zdrojový soubor v projektu, můžete vygenerovat textový soubor, který zobrazuje výsledky atribut nahrazení. Další informace o tomto postupu najdete v tématu [/Fx (sloučení vloženého kódu)](../build/reference/fx-merge-injected-code.md) a [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

Jako většina konstruktory jazyka C++ mít atributy sadu vlastností, která definuje jejich správné použití. To se označuje jako kontext atribut a je určena v tabulce atribut kontextu pro každý atribut referenční téma. Například [coclass](../windows/coclass.md) atribut lze použít pouze na existující třída nebo struktura, nikoli [cpp_quote –](../windows/cpp-quote.md) atribut, který může vložit na libovolné místo v rámci zdrojový soubor jazyka C++.

## <a name="see-also"></a>Viz také

[Koncepty](../windows/attributed-programming-concepts.md)