---
title: Aktualizace uživatelského rozhraní pro zobrazení záznamu (MFC Data Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1227ba1fe0a14af7013109b336d1d60eda41137e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizace uživatelského rozhraní pro zobrazení záznamů (Data MFC Access)
`CRecordView` poskytuje výchozí obslužné rutiny aktualizace uživatelského rozhraní pro navigační příkazy. Tyto rutiny automatizují povolení a zakázání objektů uživatelského rozhraní – položek nabídky a tlačítka panelu nástrojů. Průvodce aplikací poskytuje standardní nabídky a pokud se rozhodnete **lze ukotvit nástrojů** možnost sadu tlačítka panelu nástrojů pro příkazy. Pokud vytvoříte pomocí tříd zobrazení záznamu `CRecordView`, můžete chtít přidat podobné objekty uživatelského rozhraní do vaší aplikace.  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>Chcete-li vytvořit prostředků nabídky se v nabídce editoru  
  
1.  Odkazy na informace o používání [editor nabídek](../windows/menu-editor.md), vytvořte vlastní nabídku s stejné čtyři příkazy.  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Chcete-li vytvořit tlačítka panelu nástrojů pomocí grafického editoru  
  
1.  Odkazy na informace o používání [editor panelu nástrojů](../windows/toolbar-editor.md), upravte prostředek panelu nástrojů pro přidání tlačítka panelu nástrojů pro příkazy záznamu navigace.  
  
## <a name="see-also"></a>Viz také  
 [Podpora navigace v zobrazení záznamů](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)   
 [Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)