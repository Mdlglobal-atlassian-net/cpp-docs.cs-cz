---
title: "Atributy rozhraní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb8b42161e10aa0e6fcc06e7540487862ffc77a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="interface-attributes"></a>Atributy rozhraní
Následující atributy se používají na [rozhraní (nebo __interface)](../cpp/interface.md) C++ – klíčové slovo.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[async_uuid –](../windows/async-uuid.md)|Určuje identifikátor UUID, který přesměruje MIDL kompilátoru k definování synchronní a asynchronní verzích rozhraní modelu COM.|  
|[vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atributy.|  
|[dispinterface](../windows/dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odesílání.|  
|[duální](../windows/dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|  
|[Export](../windows/export.md)|Způsobí, že datová struktura umístit do souboru.|  
|[HelpContext –](../windows/helpcontext.md)|Určuje Identifikátor kontext, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|  
|[soubor nápovědy](../windows/helpfile.md)|Nastaví název souboru nápovědy knihovny typů.|  
|[helpstring –](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, na který se vztahuje.|  
|[helpstringcontext –](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM..|  
|[helpstringdll –](../windows/helpstringdll.md)|Určuje název knihovny DLL používat k provádění vyhledávací řetězec dokumentu (lokalizace).|  
|[skryté](../windows/hidden.md)|Určuje, že položka existuje, ale by se neměly zobrazovat v prohlížeči uživatele.|  
|[library_block –](../windows/library-block.md)|Umístí konstrukce uvnitř bloku souboru IDL knihovny.|  
|[místní](../windows/local-cpp.md)|Umožňuje použít MIDL kompilátoru jako generátor záhlaví při použití v hlavičce rozhraní. Při použití v jednotlivé funkce, označí místní postupu, pro které jsou generovány žádné zástupných procedur.|  
|[nonextensible –](../windows/nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze ji rozšířit s další členy v době běhu. Tento atribut je platné jenom pro [duální](../windows/dual.md) rozhraní.|  
|[ODL](../windows/odl.md)|Identifikuje rozhraní jako objekt popis jazyk (ODL) rozhraní.|  
|[objekt](../windows/object-cpp.md)|Určuje vlastní rozhraní.|  
|[oleautomation –](../windows/oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizace.|  
|[pointer_default –](../windows/pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatele nejvyšší úrovně, které se zobrazují v seznamy parametrů.|  
|[PTR](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|  
|[omezený](../windows/restricted.md)|Označí, kteří členové knihovny nelze volat libovolně.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu|  
  
 Musí odpovídat těchto pravidel pro definování rozhraní:  
  
-   Konvence volání výchozí hodnota je [__stdcall](../cpp/stdcall.md).  
  
-   Pokud nezadáte jeden identifikátor GUID poskytuje pro vás.  
  
-   Žádné přetížené metody jsou povoleny.  
  
 Při zadávání není [uuid](../windows/uuid-cpp-attributes.md) atribut a použití stejného názvu rozhraní v projektech jiný atribut, nevygeneruje se stejným identifikátorem GUID.  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle použití](../windows/attributes-by-usage.md)