---
title: "Atributy rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ff84939b3211633e199066e1a38da2e91efb1c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interface-attributes"></a>Atributy rozhraní
Následující atributy se používají na [rozhraní (nebo __interface)](../cpp/interface.md) C++ – klíčové slovo.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|Určuje identifikátor UUID, který přesměruje MIDL kompilátoru k definování synchronní a asynchronní verzích rozhraní modelu COM.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atributy.|  
|[dispinterface](../windows/dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odesílání.|  
|[dual](../windows/dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|  
|[export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[helpcontext](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|  
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL používat k provádění vyhledávací řetězec dokumentu (lokalizace).|  
|[hidden](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[library_block](../windows/library-block.md)|Umístí konstrukce uvnitř bloku souboru IDL knihovny.|  
|[místní](../windows/local-cpp.md)|Umožňuje použít MIDL kompilátoru jako generátor záhlaví při použití v hlavičce rozhraní. Při použití v jednotlivé funkce, označí místní postupu, pro které jsou generovány žádné zástupných procedur.|  
|[nonextensible](../windows/nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze ji rozšířit s další členy v době běhu. Tento atribut je platné jenom pro [duální](../windows/dual.md) rozhraní.|  
|[odl](../windows/odl.md)|Identifikuje rozhraní jako objekt popis jazyk (ODL) rozhraní.|  
|[object](../windows/object-cpp.md)|Určuje vlastní rozhraní.|  
|[oleautomation](../windows/oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizace.|  
|[pointer_default](../windows/pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatele nejvyšší úrovně, které se zobrazují v seznamy parametrů.|  
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|  
|[restricted](../windows/restricted.md)|Označí, kteří členové knihovny nelze volat libovolně.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu|  
  
 Musí odpovídat těchto pravidel pro definování rozhraní:  
  
-   Konvence volání výchozí hodnota je [__stdcall](../cpp/stdcall.md).  
  
-   Pokud nezadáte jeden identifikátor GUID poskytuje pro vás.  
  
-   Žádné přetížené metody jsou povoleny.  
  
 Při zadávání není [uuid](../windows/uuid-cpp-attributes.md) atribut a použití stejného názvu rozhraní v projektech jiný atribut, nevygeneruje se stejným identifikátorem GUID.  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)