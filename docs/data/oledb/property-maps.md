---
title: Mapy vlastností | Microsoft Docs
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
ms.openlocfilehash: d7664562ff31f1f5871fab4ce74c1652370a540d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103213"
---
# <a name="property-maps"></a>Mapy vlastností
Kromě relace, řádků a objekt volitelné příkazu každý poskytovatel podporuje jednu nebo více vlastností. Tyto vlastnosti jsou definovány v mapování vlastností, které jsou obsažené v souborech hlavičky generované průvodcem zprostředkovatele OLE DB. Každý hlavičkový soubor obsahuje mapu vlastností ve skupině vlastností OLE DB definované pro objekt nebo objekty definované v tomto souboru. Také obsahuje vlastnost mapy pro soubor hlaviček, který obsahuje objekt zdroje dat [vlastnosti zdroje dat](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx). Session.h obsahuje mapu vlastností pro [vlastnosti relace](https://msdn.microsoft.com/en-us/library/ms714221.aspx). Sada řádků a příkaz objekty jsou umístěny v jednom hlavičky souboru s názvem *projectname*RS.h. Tyto vlastnosti jsou členy [vlastnosti sady řádků](https://msdn.microsoft.com/en-us/library/ms711252.aspx) skupiny.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)