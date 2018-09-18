---
title: Aktualizace uživatelského rozhraní pro zobrazení záznamu (přístup k datům MFC) | Dokumentace Microsoftu
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
ms.openlocfilehash: 43f5d1017b3f89474e9dd7eebce0cf71c8c8c448
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086873"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizace uživatelského rozhraní pro zobrazení záznamu (přístup k datům MFC)

`CRecordView` poskytuje výchozí obslužné rutiny aktualizace uživatelského rozhraní pro příkazy navigace. Tyto rutiny automatizují povolování a zakazování objektů uživatelského rozhraní – položky nabídky a tlačítka panelu nástrojů. Průvodce aplikací poskytuje standardní nabídky a pokud se rozhodnete **Ukotvitelné nástrojů** možnost, sada tlačítek panelu nástrojů pro příkazy. Pokud vytvoříte pomocí tříd zobrazení záznamu `CRecordView`, můžete chtít přidat podobné objekty uživatelského rozhraní pro vaši aplikaci.  
  
### <a name="to-create-menu-resources-with-the-menu-editor"></a>Chcete-li vytvořit prostředky nabídky v nabídce editoru  
  
1. Odkaz na informace o používání [editor nabídek](../windows/menu-editor.md), vytvořte vlastní nabídku s stejné čtyř příkazů.  
  
#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Vytvoření tlačítka pomocí grafického editoru  
  
1. Odkaz na informace o používání [panelu nástrojů editoru](../windows/toolbar-editor.md), upravit prostředek panelu nástrojů přidáte tlačítka na panelu nástrojů pro příkazy navigaci.  
  
## <a name="see-also"></a>Viz také  

[Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)