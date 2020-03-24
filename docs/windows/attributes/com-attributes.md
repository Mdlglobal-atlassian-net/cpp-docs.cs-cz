---
title: COM – atributy
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: 15225d23abb66b8aadd5f82b8429334356bdaa8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168314"
---
# <a name="com-attributes"></a>COM – atributy

Atributy modelu COM vkládají kód pro podporu řady oblastí vývoje modelu COM a .NET Framework vývoje společného jazykového modulu runtime. Tyto oblasti jsou v rozsahu od implementace vlastního rozhraní a podporují existující rozhraní pro podporu uložených vlastností, metod a událostí. Kromě toho je možné najít podporu pro kompozitní a implementaci ovládacího prvku ActiveX.

|Atribut|Popis|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Označuje, že ovládací prvek lze agregovat jiným ovládacím prvkem.|
|[aggregates](aggregates.md)|Indikuje, že ovládací prvek agreguje cílovou třídu.|
|[coclass](coclass.md)|Vytvoří objekt modelu COM, který může implementovat rozhraní COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Přidá položku rozhraní do mapy modelu COM.|
|[implements_category](implements-category.md)|Určuje implementované kategorie komponent pro třídu.|
|[progid](progid.md)|Definuje ProgID pro ovládací prvek.|
|[rdx](rdx.md)|Vytvoří nebo upraví klíč registru.|
|[registration_script](registration-script.md)|Provede zadaný registrační skript.|
|[requires_category](requires-category.md)|Určuje požadované kategorie komponent pro třídu.|
|[support_error_info](support-error-info.md)|Podporuje zasílání zpráv o chybách pro cílový objekt.|
|[synchronize](synchronize.md)|Synchronizuje přístup k metodě.|
|[threading](threading-cpp.md)|Určuje model dělení na vlákna pro objekt modelu COM.|
|[vi_progid](vi-progid.md)|Definuje ProgID, který je nezávislý na verzi ovládacího prvku.|

## <a name="see-also"></a>Viz také

[Atributy podle skupin](attributes-by-group.md)
