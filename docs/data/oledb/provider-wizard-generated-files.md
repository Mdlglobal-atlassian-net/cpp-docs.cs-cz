---
title: Poskytovatel souborů vytvořených průvodcem
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 0638680482546f56f26b70660ab43bd9848438a3
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707474"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem

::: moniker range="vs-2019"

Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

**Průvodce zprostředkovatelem ATL OLE DB** generuje následující soubory. V následujících tématech použijte krátký název *vlastní*, ale názvy souborů závisí na volby provedené při vytváření zprostředkovatele.

|Název souboru|Popis|
|---------------|-----------------|
|*Custom*RS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapování sloupců zprostředkovatele.|
|*Vlastní*DS.h|Implementuje objekt zdroje dat. Tento soubor hlavičky obsahuje vlastnosti zdroje dat na mapě vlastnost.|
|*Vlastní*RS.h|Implementuje objekty příkazu a sady řádků. Tento soubor hlavičky obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|
|*Vlastní*Sess.h|Implementuje objekt relace. Tento soubor hlavičky obsahuje mapování vlastnosti pro vlastnosti relace.|
|*Vlastní*.rgs|Obsahuje objekty registrované generovaných **Průvodce zprostředkovatelem technologie OLE DB**.|

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
