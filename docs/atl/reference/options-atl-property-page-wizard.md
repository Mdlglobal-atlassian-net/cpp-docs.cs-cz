---
title: Možnosti, Průvodce stránkou vlastností ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: a46a55cca221293e83a72bf0c2670e2343c744b0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076214"
---
# <a name="options-atl-property-page-wizard"></a>Možnosti, Průvodce stránkou vlastností ATL

::: moniker range="vs-2019"

Průvodce stránkou vlastností ATL není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Pomocí této stránky průvodce můžete definovat model vláken a úroveň agregace stránky vlastností, kterou vytváříte.

- **Model vláken**

   Určuje model vláken používaný na stránce vlastností.

   Další informace najdete v tématu [Určení modelu vláken v projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) .

   |Možnost|Popis|
   |------------|-----------------|
   |**Konkrétní**|Stránka vlastností se spouští pouze v primárním vlákně COM.|
   |**Domy**|Stránku vlastností lze vytvořit v jakémkoli vláknovém izolovaném vlákně. Výchozí nastavení|

- **Agregace**

   Přidá podporu agregace pro stránku vlastností, kterou vytváříte. Další informace najdete v tématu [agregace](../../atl/aggregation.md) .

   |Možnost|Popis|
   |------------|-----------------|
   |**Ano**|Vytvoří stránku vlastností, která se dá agregovat.|
   |**Ne**|Vytvoří stránku vlastností, kterou nelze agregovat.|
   |**Pouze**|Vytvoří stránku vlastností, která se dá vytvořit jenom pomocí agregace.|

::: moniker-end

## <a name="see-also"></a>Viz také

[Průvodce stránkou vlastností ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Řetězce, Průvodce stránkou vlastností ATL](../../atl/reference/strings-atl-property-page-wizard.md)
