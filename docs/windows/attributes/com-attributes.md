---
title: Com – atributy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
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
ms.openlocfilehash: 2aa88f88fe26b96202f2a917bddf5c8bb07c0d3c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071125"
---
# <a name="com-attributes"></a>COM – atributy

Com – atributy vložení kódu pro podporu mnoha oblastech COM vývoj a rozhraní .NET Framework common language runtime. Tyto oblasti sahají od implementace vlastního rozhraní a podporu existující rozhraní podporující uložené vlastnosti, metody a události. Kromě toho podpory najdete složeného a implementaci ovládacího prvku ActiveX.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že ovládací prvek se dají agregovat jiný ovládací prvek.|
|[aggregates](aggregates.md)|Označuje, že ovládací prvek agreguje cílové třídy.|
|[coclass](coclass.md)|Vytvoří objekt modelu COM, které můžete implementovat rozhraní modelu COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku do rozhraní COM mapy.|
|[implements_category](implements-category.md)|Určuje kategorie implementované součásti pro třídu.|
|[progid](progid.md)|Definuje identifikátor ProgID ovládacího prvku.|
|[rdx](rdx.md)|Vytvoří nebo změní klíče registru.|
|[registration_script](registration-script.md)|Provede zadanou registraci skript.|
|[requires_category](requires-category.md)|Určuje požadovanou součást kategorie pro třídu.|
|[support_error_info](support-error-info.md)|Podporuje odesílání sestav chyb pro cílový objekt.|
|[synchronize](synchronize.md)|Synchronizuje přístup k metodě.|
|[threading](threading-cpp.md)|Určuje model vláken pro objekt modelu COM.|
|[vi_progid](vi-progid.md)|Definuje identifikátor ProgID nezávislé na verzi pro ovládací prvek.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)