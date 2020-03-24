---
title: Aktualizace uživatelského rozhraní pro zobrazení záznamů (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209050"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Aktualizace uživatelského rozhraní pro zobrazení záznamů (přístup k datům MFC)

`CRecordView` poskytuje výchozí obslužné rutiny aktualizace uživatelského rozhraní pro navigační příkazy. Tyto obslužné rutiny automatizují povolení a zakázání objektů uživatelského rozhraní – položky nabídky a tlačítka panelu nástrojů. Průvodce aplikací poskytuje standardní nabídky a, pokud zvolíte možnost **panel nástrojů ukotvit** , sada tlačítek panelu nástrojů pro příkazy. Pokud vytvoříte třídu zobrazení záznamu pomocí `CRecordView`, může být vhodné přidat podobné objekty uživatelského rozhraní do aplikace.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Vytvoření prostředků nabídky pomocí editoru nabídek

1. Odkaz na informace o použití [editoru nabídek](../windows/menu-editor.md)získáte tak, že vytvoříte vlastní nabídku se stejnými čtyřmi příkazy.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Vytvoření tlačítek panelu nástrojů pomocí grafického editoru

1. Odkazy na informace o použití [editoru panelu nástrojů](../windows/toolbar-editor.md)získáte úpravou prostředku panelu nástrojů pro přidání tlačítek panelu nástrojů pro navigační příkazy záznamů.

## <a name="see-also"></a>Viz také

[Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Používání zobrazení záznamu](../data/using-a-record-view-mfc-data-access.md)
