---
title: Základní mechanismy atributů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6db2994a2606f6c4d0cb4cd581ec46d87ca3d2c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864931"
---
# <a name="basic-mechanics-of-attributes"></a>Základní mechanismy atributů
Existují tři způsoby, jak vložit atributy do projektu. První můžete je ručně do zdrojového kódu. Druhý můžete vložit pomocí mřížku vlastností objektu ve vašem projektu. Nakonec můžete vložit pomocí různých průvodců. Další informace o používání okno Vlastnosti a různých průvodců najdete v tématu [vytváření a správa projekty Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 Jako dříve, při sestavení projektu kompilátor analyzuje každý C++ zdrojový soubor, který vytvořil soubor objektu. Ale když kompilátor zaznamená atributu, je analyzovat a syntakticky ověřit. Kompilátor pak zavolá dynamicky poskytovatele atribut pro vložení kódu a provádět další úpravy v době kompilace. Implementace zprostředkovatele se liší v závislosti na typu atributu. Například Atlprov.dll implementují související ATL atributy.  
  
 Následující obrázek ukazuje vztah mezi kompilátoru a poskytovatele atribut.  
  
 ![Součást atribut komunikace](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  Použití atributu nezmění obsah zdrojového souboru. Během ladění relace je jenom čas, kdy kód vygenerovaný atribut je viditelné. Kromě toho pro každý zdrojový soubor v projektu, může generovat textový soubor, který se zobrazí výsledky nahrazení atribut. Další informace o tomto postupu najdete v tématu [/Fx (sloučení vloženého kódu)](../build/reference/fx-merge-injected-code.md) a [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).  
  
 Většina C++ konstrukce, jako je mít atributy sada vlastností, které definuje jejich správné využití. To se označuje jako kontext atribut a je určeno v tabulce kontext atribut pro každý atribut referenční téma. Například [třída typu coclass](../windows/coclass.md) atribut lze použít pouze do existující třídy nebo struktura, nikoli [cpp_quote –](../windows/cpp-quote.md) atribut, který lze vložit kdekoli v rámci C++ zdrojového souboru.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../windows/attributed-programming-concepts.md)