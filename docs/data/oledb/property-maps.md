---
title: Mapy vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c6c3ddc4b19cd9b65203d8a5e675b9ed75720a1
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216458"
---
# <a name="property-maps"></a>Mapy vlastností

Každý poskytovatel relace, řádků a objekt volitelný příkaz, podporuje jednu nebo více vlastností. Tyto vlastnosti jsou definovány v rámci služby maps vlastnosti uložené v souborech hlaviček, které jsou vytvořené **Průvodce zprostředkovatelem technologie OLE DB**. Každý soubor hlavičky obsahuje mapování vlastností ve skupině vlastností OLE DB pro objekt nebo objekty definované v tomto souboru definován. Hlavičkový soubor, který obsahuje objekt zdroje dat také obsahuje vlastnosti mapy [vlastnosti DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` obsahuje vlastnosti mapy [vlastnosti relace](/previous-versions/windows/desktop/ms714221). Objekty sady řádků a příkaz se v jedné hlavičce souboru s názvem *projectname*RS.h. Tyto vlastnosti jsou členy [vlastnosti sady řádků](/previous-versions/windows/desktop/ms711252) skupiny.

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
