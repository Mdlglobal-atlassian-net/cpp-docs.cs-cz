---
title: Mapy vlastností
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501290"
---
# <a name="property-maps"></a>Mapy vlastností

V případě relace, sady řádků a volitelného objektu příkazu podporuje každý zprostředkovatel jednu nebo více vlastností. Tyto vlastnosti jsou definované v mapách vlastností uložených v hlavičkových souborech vytvořených průvodcem **poskytovatelem OLE DB**. Každý hlavičkový soubor obsahuje mapu pro vlastnosti ve skupině vlastností OLE DB definované pro objekt nebo objekty definované v tomto souboru. Hlavičkový soubor, který obsahuje objekt zdroje dat, také obsahuje mapu vlastností [vlastností zdroje](/previous-versions/windows/desktop/ms724188(v=vs.85))dat. `Session.h`obsahuje mapu vlastností pro [vlastnosti relace](/previous-versions/windows/desktop/ms714221(v=vs.85)). Sada řádků a objektů příkazu jsou v jednom hlavičkovém souboru s názvem *ProjectName*RS. h. Tyto vlastnosti jsou členy skupiny [vlastností sady řádků](/previous-versions/windows/desktop/ms711252(v=vs.85)) .

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
