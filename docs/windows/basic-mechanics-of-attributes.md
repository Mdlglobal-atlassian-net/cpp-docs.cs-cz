---
title: "Základní mechanismy atributů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99771e798e4957de5ff69601a5d3494e5fcacc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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