---
title: Vytvoření zprostředkovatele | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b08d2a2f68d174ae7c92d1d6bc0fa2bbb764fdca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097182"
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