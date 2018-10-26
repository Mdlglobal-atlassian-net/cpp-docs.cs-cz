---
title: Mapy vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: bbed70f7871cb215a944a5143793b26b4196d7bc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052746"
---
# <a name="property-maps"></a>Mapy vlastností

Kromě relace, řádků a objekt volitelný příkaz každý poskytovatel podporuje jednu nebo více vlastností. Tyto vlastnosti jsou definované v rámci služby maps vlastnosti obsažené v souborech hlaviček vytvořené průvodcem zprostředkovatele OLE DB. Každý soubor hlavičky obsahuje mapování vlastností ve skupině vlastností OLE DB pro objekt nebo objekty definované v tomto souboru definován. Hlavičkový soubor, který obsahuje objekt zdroje dat také obsahuje vlastnosti mapy [vlastnosti DataSource](https://msdn.microsoft.com/library/ms724188). Session.h obsahuje vlastnost mapy [vlastnosti relace](/previous-versions/windows/desktop/ms714221). Objekty sady řádků a příkaz se nacházejí v jedné hlavičce souboru s názvem *projectname*RS.h. Tyto vlastnosti jsou členy [vlastnosti sady řádků](/previous-versions/windows/desktop/ms711252) skupiny.

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)