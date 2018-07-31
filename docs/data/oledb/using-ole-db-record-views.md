---
title: Použití zobrazení záznamů technologie OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d98b2f95c9b06d748b7486955b03f34f41e9ab57
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339510"
---
# <a name="using-ole-db-record-views"></a>Použití zobrazení záznamů technologie OLE DB
Pokud chcete zobrazit data sady řádků OLE DB v aplikaci knihovny MFC, měli byste použít třídy MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Vytvořit zobrazení záznamu objekt z `COleDBRecordView` umožňuje zobrazit záznamy databáze v MFC – ovládací prvky. Zobrazení záznamů je přímo připojený k objektu sady řádků technologie OLE DB, který je vytvořený z formulářové zobrazení dialogového okna `CRowset` šablony třídy. Získání popisovač objektu sady řádků je jednoduchý:  
  
```cpp  
COleDBRecordView myRecordView;  
...  
// CProductAccessor is a user record class  
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();  
```  
  
 Zobrazí pole `CRowset` objektu v ovládacích prvcích v dialogovém okně. `COleDBRecordView` Objekt používá dialogové okno Data DDX (Exchange) a navigační funkce součástí `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, a `MoveLast`) k automatizaci přesouvání dat mezi ovládacími prvky ve formuláři pole a sady řádků. `COleDBRecordView` uchovává informace o poloze uživatele v dané sadě řádků tak, aby uživatelské rozhraní a poskytuje lze aktualizovat zobrazení záznamu [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) aktualizovat aktuální záznam před přesunutím do jiné.  
  
 Můžete použít funkce DDX s `COleDbRecordView` získat data přímo ze sady záznamů databáze a zobrazit je v ovládacím prvku dialogu. Byste měli použít **DDX_\***  metody (jako `DDX_Text`), nikoli **DDX_Field –\***  funkce (například `DDX_FieldText`) s `COleDbRecordView`.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)   
 [COleDBRecordView – třída](../../mfc/reference/coledbrecordview-class.md)