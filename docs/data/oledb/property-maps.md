---
title: Mapy vlastností
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 9df98dc85c9242693319542cea0730341d87a052
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035371"
---
# <a name="property-maps"></a>Mapy vlastností

Každý poskytovatel relace, řádků a objekt volitelný příkaz, podporuje jednu nebo více vlastností. Tyto vlastnosti jsou definovány v rámci služby maps vlastnosti uložené v souborech hlaviček, které jsou vytvořené **Průvodce zprostředkovatelem technologie OLE DB**. Každý soubor hlavičky obsahuje mapování vlastností ve skupině vlastností OLE DB pro objekt nebo objekty definované v tomto souboru definován. Hlavičkový soubor, který obsahuje objekt zdroje dat také obsahuje vlastnosti mapy [vlastnosti DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` obsahuje vlastnosti mapy [vlastnosti relace](/previous-versions/windows/desktop/ms714221(v=vs.85)). Objekty sady řádků a příkaz se v jedné hlavičce souboru s názvem *projectname*RS.h. Tyto vlastnosti jsou členy [vlastnosti sady řádků](/previous-versions/windows/desktop/ms711252(v=vs.85)) skupiny.

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
