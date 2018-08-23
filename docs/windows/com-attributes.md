---
title: Com – atributy | Dokumentace Microsoftu
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
ms.openlocfilehash: 857e032f02102a79747b79140207d07905f5b3d2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591588"
---
# <a name="com-attributes"></a>COM – atributy
Com – atributy vložení kódu pro podporu mnoha oblastech COM vývoj a rozhraní .NET Framework common language runtime. Tyto oblasti sahají od implementace vlastního rozhraní a podporu existující rozhraní podporující uložené vlastnosti, metody a události. Kromě toho podpory najdete složeného a implementaci ovládacího prvku ActiveX.
  
|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Označuje, že ovládací prvek se dají agregovat jiný ovládací prvek.|
|[aggregates](../windows/aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[coclass](../windows/coclass.md)|Vytvoří objekt modelu COM, které můžete implementovat rozhraní modelu COM.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[implements_category](../windows/implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[progid](../windows/progid.md)|Definuje identifikátor ProgID ovládacího prvku.|
|[rdx](../windows/rdx.md)|Vytvoří nebo změní klíče registru.|
|[registration_script](../windows/registration-script.md)|Provede zadanou registraci skript.|
|[requires_category](../windows/requires-category.md)|Určuje požadovanou součást kategorie pro třídu.|
|[support_error_info](../windows/support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|
|[synchronize](../windows/synchronize.md)|Synchronizuje přístup k metodě.|
|[Dělení na vlákna](../windows/threading-cpp.md)|Určuje model vláken pro objekt modelu COM.|
|[vi_progid](../windows/vi-progid.md)|Definuje identifikátor ProgID nezávislé na verzi pro ovládací prvek.|
  
## <a name="see-also"></a>Viz také
 [Atributy podle skupin](../windows/attributes-by-group.md)