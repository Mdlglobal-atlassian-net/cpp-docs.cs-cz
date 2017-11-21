---
title: Zdroje dat a relace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 500ed062dd81681466ada4c749f8a835b9822cb2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-sources-and-sessions"></a>Zdroje dat a relace
Následující obrázek ukazuje třídy, které podporují připojení k a přístup ke zdroji dat. Každá třída je založen na standardní součást implementace technologie OLE DB.  
  
 ![Datové zdroje a relace třídy](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
Zdroj dat a relace třídy  
  
 Třídy jsou:  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md) Tato třída se vytvoří objekt zdroje dat, které vytváří a spravuje připojení ke zdroji dat pomocí zprostředkovatele OLE DB. Zdroj dat trvá informace, jako jsou informace datového zdroje adresu a ověřování ve formě připojovací řetězec.  
  
     Je také to, že pomocná třída [CEnumerator](../../data/oledb/cenumerator-class.md) se často používá před žádné připojení k získání seznamu dostupných zprostředkovatelů zaregistrován v systému. To umožňuje vybrat jako zdroj dat zprostředkovatele. Například **vlastnosti propojení dat** dialogové okno používá tuto třídu k naplnění seznamu zprostředkovatelů na **zprostředkovatelé** kartě. Ta je ekvivalentní **SQLBrowseConnect** nebo **SQLDriverConnect** funkce.  
  
-   [CSession](../../data/oledb/csession-class.md) objekt relace, který představuje relaci jednoho přístupu ke zdroji dat se vytvoří instance této třídy. Ve zdroji dat však můžete vytvořit více relací. Pro každou relaci můžete vytvořit sady řádků, příkazy a další objekty, pro přístup k datům ze zdroje dat. Relace zpracovává transakce.  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)