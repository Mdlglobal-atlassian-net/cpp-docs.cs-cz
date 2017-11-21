---
title: "Samostatné atributy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17009c1e9c1f7a771b717a96d1aadc4a680fe78f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stand-alone-attributes"></a>Samostatné atributy
Atribut samostatné nefunguje na klíčové slovo C++ ale se víc podobá řádku kódu. Atribut samostatné příkazy vyžadují středníkem na konci řádku.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[cpp_quote –](../windows/cpp-quote.md)|Zadaný řetězec bez znaky uvozovek za sebou vysílá do souboru generovaného záhlaví.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|  
|[emitidl –](../windows/emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracovat a uložena v souboru generovaného IDL.|  
|[idl_module –](../windows/idl-module.md)|Určuje vstupní bod v knihovně DLL.|  
|[idl_quote –](../windows/idl-quote.md)|Umožňuje používat IDL konstrukce, které nejsou podporované v aktuální verzi Visual C++ a jejich předání do souboru generovaného IDL.|  
|[Import](../windows/import.md)|Určuje jiný .idl, .odl nebo .h soubor obsahující definice, které chcete odkazovat z hlavní .idl souboru.|  
|[importidl –](../windows/importidl.md)|Vloží zadaný .idl souboru do souboru generovaného .idl|  
|[importlib –](../windows/importlib.md)|Díky typy, které již byly kompilovány do jiného typu knihovny k dispozici pro knihovny typů vytváří.|  
|[Zahrnout](../windows/include-cpp.md)|Určuje jeden nebo více soubory hlaviček, které mají být zahrnuty v souboru generovaného .idl.|  
|[includelib –](../windows/includelib-cpp.md)|Způsobí, že mají být zahrnuty v souboru generovaného .idl .idl nebo .h soubor.|  
|[library_block –](../windows/library-block.md)|Umístí konstrukce uvnitř bloku souboru IDL knihovny.|  
|[modul](../windows/module-cpp.md)|Knihovna bloku definuje v souboru.|  
|[no_injected_text –](../windows/no-injected-text.md)|Kompilátor brání vložení kódu v důsledku použití atributu.|  
|[Direktiva pragma](../windows/pragma.md)|Do souboru generovaného .idl vysílá zadaný řetězec bez znaky uvozovek za sebou.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)