---
title: "Vytvoření zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: feec2aa1e3f9d50c8737420d0049d8bcf658eac2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatele OLE DB knihovny ATL  
  
1.  Klikněte pravým tlačítkem na projekt.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat třídu**.  
  
3.  V **přidat třídu** dialogové okno, vyberte **ATL zprostředkovatele technologie OLE DB** ikonu a pak klikněte na tlačítko **otevřete**.  
  
4.  V průvodci zprostředkovatele knihovny ATL technologie OLE DB zadejte krátký název svého poskytovatele v **krátký název** pole. V následujících tématech použijte krátký název "MyProvider", ale můžete použít jiný název. Další pole názvů naplnit podle názvu, který zadáte.  
  
5.  V případě potřeby upravte další pole názvů. Kromě název objektu a soubor můžete upravit následující:  
  
    -   **Třída typu coclass**: název, který COM používá k vytvoření zprostředkovatele.  
  
    -   **ProgID**: programové identifikátor, který je textový řetězec, který lze použít místo identifikátor GUID.  
  
    -   **Verze**: použity s ProgID a třída typu coclass pro generování ID programový závislý na verzi.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)