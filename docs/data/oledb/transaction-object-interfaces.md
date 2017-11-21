---
title: "Rozhraní objektu transakce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5731d4d187fa02b0b68c9e4b764bf9aeb1f653dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="transaction-object-interfaces"></a>Rozhraní objektu transakce
Transakční objekt definuje atomické jednotky práce na zdroj dat a určuje, jak tyto jednotky vztahují k sobě navzájem. Tento objekt není přímo podporována šablony zprostředkovatele technologie OLE DB (to znamená, musíte vytvořit vlastní objekt).  
  
 V následující tabulce jsou povinné a nepovinné rozhraní definované OLE DB pro transakční objekt.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Povinné|Ne|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Povinné|Ne|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Nepovinné|Ne|  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)