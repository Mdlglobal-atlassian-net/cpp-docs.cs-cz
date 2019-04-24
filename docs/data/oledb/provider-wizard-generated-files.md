---
title: Poskytovatel souborů vytvořených průvodcem
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: a9a706463326249135a55bc907cb8a664a3ca808
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282959"
---
# <a name="provider-wizard-generated-files"></a>Poskytovatel souborů vytvořených průvodcem

**Průvodce zprostředkovatelem ATL OLE DB** generuje následující soubory. V následujících tématech použijte krátký název *vlastní*, ale názvy souborů závisí na volby provedené při vytváření zprostředkovatele.

|Název souboru|Popis|
|---------------|-----------------|
|*Custom*RS.cpp|Obsahuje pomocné rutiny příkaz `Execute` metoda a mapování sloupců zprostředkovatele.|
|*Vlastní*DS.h|Implementuje objekt zdroje dat. Tento soubor hlavičky obsahuje vlastnosti zdroje dat na mapě vlastnost.|
|*Vlastní*RS.h|Implementuje objekty příkazu a sady řádků. Tento soubor hlavičky obsahuje mapu vlastností pro sadu řádků a příkaz Vlastnosti.|
|*Vlastní*Sess.h|Implementuje objekt relace. Tento soubor hlavičky obsahuje mapování vlastnosti pro vlastnosti relace.|
|*Vlastní*.rgs|Obsahuje objekty registrované generovaných **Průvodce zprostředkovatelem technologie OLE DB**.|

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
