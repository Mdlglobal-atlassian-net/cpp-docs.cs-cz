---
title: COM – atributy
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: fa7e279f6b7c9c0932d404c336bcfd89bfd553a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644090"
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