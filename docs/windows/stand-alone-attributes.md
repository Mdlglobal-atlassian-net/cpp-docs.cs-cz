---
title: Samostatné atributy | Microsoft Docs
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
ms.openlocfilehash: 59846b1ca031cc02c85cb6ace23f96e8c5cc9f37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890425"
---
# <a name="stand-alone-attributes"></a>Samostatné atributy
Atribut samostatné nefunguje na klíčové slovo C++ ale se víc podobá řádku kódu. Atribut samostatné příkazy vyžadují středníkem na konci řádku.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[cpp_quote](../windows/cpp-quote.md)|Zadaný řetězec bez znaky uvozovek za sebou vysílá do souboru generovaného záhlaví.|  
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atribut.|  
|[db_command](../windows/db-command.md)|Vytvoří příkaz OLE DB.|  
|[emitidl](../windows/emitidl.md)|Určuje, zda všechny následné IDL – atributy zpracovat a uložena v souboru generovaného IDL.|  
|[idl_module](../windows/idl-module.md)|Určuje vstupní bod v knihovně DLL.|  
|[idl_quote](../windows/idl-quote.md)|Umožňuje používat IDL konstrukce, které nejsou podporované v aktuální verzi Visual C++ a jejich předání do souboru generovaného IDL.|  
|[import](../windows/import.md)|Určuje jiný .idl, .odl nebo .h soubor obsahující definice, které chcete odkazovat z hlavní .idl souboru.|  
|[importidl](../windows/importidl.md)|Vloží zadaný .idl souboru do souboru generovaného .idl|  
|[importlib](../windows/importlib.md)|Díky typy, které již byly kompilovány do jiného typu knihovny k dispozici pro knihovny typů vytváří.|  
|[Zahrnout](../windows/include-cpp.md)|Určuje jeden nebo více soubory hlaviček, které mají být zahrnuty v souboru generovaného .idl.|  
|[includelib –](../windows/includelib-cpp.md)|Způsobí, že mají být zahrnuty v souboru generovaného .idl .idl nebo .h soubor.|  
|[library_block](../windows/library-block.md)|Umístí konstrukce uvnitř bloku souboru IDL knihovny.|  
|[Modul](../windows/module-cpp.md)|Knihovna bloku definuje v souboru.|  
|[no_injected_text](../windows/no-injected-text.md)|Kompilátor brání vložení kódu v důsledku použití atributu.|  
|[pragma](../windows/pragma.md)|Do souboru generovaného .idl vysílá zadaný řetězec bez znaky uvozovek za sebou.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)