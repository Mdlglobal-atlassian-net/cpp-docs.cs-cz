---
title: Možnosti Průvodce stránkou vlastností ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c883b3e79bd857bb457da0a1bd540a08ddddf017
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524545"
---
# <a name="options-atl-property-page-wizard"></a>Možnosti Průvodce stránkou vlastností ATL


::: moniker range="vs-2019"

Průvodce stránkou vlastností ATL není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="vs-2017"

Pomocí této stránky v průvodci můžete definovat vláken modelu a agregace úroveň stránky vlastností, kterou vytváříte.

- **Model vláken**

   Určuje model vláken používané stránky vlastností.

   Zobrazit [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) Další informace.

   |Možnost|Popis|
   |------------|-----------------|
   |**Jeden**|Na stránce vlastností spustí jenom v primárním vláknu COM.|
   |**Apartment**|Na stránce vlastností lze vytvořit v libovolné objektu apartment pro jedno vlákno. Výchozí nastavení|

- **Agregace**

   Přidá podporu agregace pro stránku vlastnost, kterou vytváříte. Zobrazit [agregace](../../atl/aggregation.md) Další informace.

   |Možnost|Popis|
   |------------|-----------------|
   |**Ano**|Vytvoření stránky vlastností, které se dají agregovat.|
   |**Ne**|Vytvoření stránky vlastností, který nemůže být agregován.|
   |**Pouze**|Vytvoření stránky vlastností, který může být vytvořena pouze prostřednictvím agregace.|

::: moniker-end

## <a name="see-also"></a>Viz také:

[Průvodce stránkou vlastností ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Řetězce, Průvodce stránkou vlastností ATL](../../atl/reference/strings-atl-property-page-wizard.md)
