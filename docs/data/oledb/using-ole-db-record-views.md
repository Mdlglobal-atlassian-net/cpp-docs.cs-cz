---
title: Použití zobrazení záznamů technologie OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB record views
- COleDBRecordView class, overview
- rowsets, record views
- record views, record view objects
- OLE DB, record views
- MFC, record views
ms.assetid: 1cd3e595-ce08-43d8-a0a9-d03b5d3e24ce
ms.openlocfilehash: 83f4d64252ab5c2b80d62419ea448c1ffd0cdd69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375181"
---
# <a name="using-ole-db-record-views"></a>Použití zobrazení záznamů technologie OLE DB

Pokud chcete zobrazit data sady řádků OLE DB v aplikaci knihovny MFC, použijte třídy knihovny MFC [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md). Vytvořit zobrazení záznamu objekt z `COleDBRecordView` umožňuje zobrazit záznamy databáze v MFC – ovládací prvky. Zobrazení záznamů je přímo připojený k objektu sady řádků technologie OLE DB, který je vytvořený z formulářové zobrazení dialogového okna `CRowset` šablony třídy. Získání popisovač objektu sady řádků je jednoduchý:

```cpp
COleDBRecordView myRecordView;
...
// CProductAccessor is a user record class
CRowset<CAccessor<CProductAccessor>> myRowSet = myRecordView.OnGetRowset();
```

Zobrazí pole `CRowset` objektu v ovládacích prvcích v dialogovém okně. `COleDBRecordView` Objekt používá dialogové okno Data DDX (Exchange) a navigační funkce součástí `CRowset` (`MoveFirst`, `MoveNext`, `MovePrev`, a `MoveLast`) k automatizaci přesouvání dat mezi ovládacími prvky ve formuláři pole a sady řádků. `COleDBRecordView` uchovává informace o poloze uživatele v dané sadě řádků tak, aby uživatelské rozhraní a poskytuje lze aktualizovat zobrazení záznamu [OnMove](../../mfc/reference/coledbrecordview-class.md#onmove) aktualizovat aktuální záznam před přesunutím do jiné.

Můžete použít funkce DDX s `COleDbRecordView` získat data přímo ze sady záznamů databáze a zobrazit je v ovládacím prvku dialogu. Použití **DDX_** <strong>\*</strong> metody (například `DDX_Text`), nikoli **DDX_Field** <strong>\*</strong> funkcí ( například `DDX_FieldText`) s `COleDbRecordView`.

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)<br/>
[COleDBRecordView – třída](../../mfc/reference/coledbrecordview-class.md)<br/>
