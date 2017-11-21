---
title: "COM – atributy | Microsoft Docs"
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
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f9cd3657426a2a51a582ab695376287a3e975056
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="com-attributes"></a>COM – atributy
Atributy COM vloží kód pro podporu mnoha oblastech vývoj COM a rozhraní .NET Framework common language runtime vývoj. Tyto oblasti v rozsahu od implementace vlastní rozhraní a podporu existující rozhraní podpory uložených vlastností, metod a události. Kromě toho podporu naleznete složené a implementaci ovládacího prvku ActiveX.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[agregovatelné](../windows/aggregatable.md)|Označuje, že ovládacího prvku se dají agregovat v další ovládací prvek.|  
|[agregace](../windows/aggregates.md)|Označuje, že ovládacího prvku agreguje cílové třídy.|  
|[Třída typu coclass](../windows/coclass.md)|Vytvoří objekt COM, které můžete implementovat rozhraní modelu COM.|  
|[COM_INTERFACE_ENTRY –](../windows/com-interface-entry-cpp.md)|Přidá položku rozhraní COM mapu.|  
|[implements_category –](../windows/implements-category.md)|Určuje implementovaná součást kategorie pro třídu.|  
|[ProgID](../windows/progid.md)|Definuje ProgID pro ovládací prvek.|  
|[RDX –](../windows/rdx.md)|Vytvoří nebo upraví klíč registru.|  
|[registration_script –](../windows/registration-script.md)|Spustí skript zadanou registraci.|  
|[requires_category –](../windows/requires-category.md)|Určuje požadovanou součást kategorie pro třídu.|  
|[support_error_info –](../windows/support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|  
|[Synchronizovat](../windows/synchronize.md)|Synchronizuje přístup k metodě.|  
|[dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro objekt COM.|  
|[vi_progid –](../windows/vi-progid.md)|Definuje ProgID nezávislé na verzi pro ovládací prvek.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle skupin](../windows/attributes-by-group.md)