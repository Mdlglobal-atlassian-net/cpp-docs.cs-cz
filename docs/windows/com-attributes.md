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
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71ff4e3fdb80b48e306e543bdb683c3dd2b26ec3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443329"
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