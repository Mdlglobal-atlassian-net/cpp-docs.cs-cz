---
title: COM – atributy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d37ba5c690b61840ad261e6ab966d0cc74c07c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="com-attributes"></a>COM – atributy
Atributy COM vloží kód pro podporu mnoha oblastech vývoj COM a rozhraní .NET Framework common language runtime vývoj. Tyto oblasti v rozsahu od implementace vlastní rozhraní a podporu existující rozhraní podpory uložených vlastností, metod a události. Kromě toho podporu naleznete složené a implementaci ovládacího prvku ActiveX.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Označuje, že ovládacího prvku se dají agregovat v další ovládací prvek.|  
|[aggregates](../windows/aggregates.md)|Označuje, že ovládacího prvku agreguje cílové třídy.|  
|[coclass](../windows/coclass.md)|Vytvoří objekt COM, které můžete implementovat rozhraní modelu COM.|  
|[COM_INTERFACE_ENTRY –](../windows/com-interface-entry-cpp.md)|Přidá položku rozhraní COM mapu.|  
|[implements_category](../windows/implements-category.md)|Určuje implementovaná součást kategorie pro třídu.|  
|[progid](../windows/progid.md)|Definuje ProgID pro ovládací prvek.|  
|[rdx](../windows/rdx.md)|Vytvoří nebo upraví klíč registru.|  
|[registration_script](../windows/registration-script.md)|Spustí skript zadanou registraci.|  
|[requires_category](../windows/requires-category.md)|Určuje požadovanou součást kategorie pro třídu.|  
|[support_error_info](../windows/support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|  
|[synchronize](../windows/synchronize.md)|Synchronizuje přístup k metodě.|  
|[Dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro objekt COM.|  
|[vi_progid](../windows/vi-progid.md)|Definuje ProgID nezávislé na verzi pro ovládací prvek.|  
  
## <a name="see-also"></a>Viz také  
 [Atributy podle skupin](../windows/attributes-by-group.md)