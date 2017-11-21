---
title: "Použití zobrazení záznamů technologie OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4e57f320c8b207e7b1c8721ab25744cd1f128bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-ole-db-record-views"></a>Použití zobrazení záznamů technologie OLE DB
Pokud chcete zobrazit data sady řádků OLE DB v aplikaci MFC, měli byste použít třídu MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Objekt zobrazení záznamu vytvořit z `COleDBRecordView` umožňuje zobrazit záznamy databáze v MFC – ovládací prvky. Zobrazení záznamů je přímo připojený k objektu sady řádků technologie OLE DB, který je vytvořený z zobrazení formuláře dialogové okno `CRowset` třídy šablony. Získání popisovače na objektu sady řádků je jednoduchý:  
  
```  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 V zobrazení je zobrazeno pole `CRowset` objektu v ovládacích prvcích dialogovém okně. `COleDBRecordView` Objektu používá dialogové okno Exchange DDX (Data) a navigačních funkce součástí `CRowset` (**MoveFirst**, `MoveNext`, `MovePrev`, a `MoveLast`) k automatizaci přesouvání dat mezi ovládacími prvky na formuláři a pole sady řádků. `COleDBRecordView`uchovává informace o pozici uživatele v dané sadě řádků tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní a zdroje [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) metoda pro aktualizaci na aktuální záznam před přesunutím do jiné.  
  
 Můžete použít funkce DDX s **COleDbRecordView** získat data přímo ze záznamů databáze a zobrazit ji v dialogovém okně ovládacího prvku. Byste měli používat **DDX_\***  metody (například `DDX_Text`), nikoli **DDX_Field –\***  funkce (například `DDX_FieldText`) s **COleDbRecordView** .  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)   
 [COleDBRecordView – třída](../../mfc/reference/coledbrecordview-class.md)