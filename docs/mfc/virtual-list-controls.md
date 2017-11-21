---
title: "Ovládací prvky typu virtuální seznam | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2853c40a5eaa3ccb8dbbf5855b92b4cba9b3a140
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="virtual-list-controls"></a>Ovládací prvky typu virtuální seznam
Ovládacího prvku typu virtuální seznam je zobrazení ovládací prvek seznamu, který má **LVS_OWNERDATA** stylu. Tento styl umožňuje kontrolu pro podporu až počet položek `DWORD` (počet položek výchozí rozšiřuje pouze k `int`). Možnost mít pouze podmnožinu dat položky do paměti v jednom okamžiku je však největších výhod poskytované tento styl. To umožňuje ovládacího prvku zobrazení virtuální seznam jít pro použití s velké databáze informací, kde konkrétní metody přístupu k datům, jsou již na místě.  
  
> [!NOTE]
>  Kromě zajištění seznam virtuálních funkcí v `CListCtrl`, MFC také poskytuje stejnou funkcionalitu v [CListView](../mfc/reference/clistview-class.md) třídy.  
  
 Existují některé problémy s kompatibilitou, které byste měli vědět, když vývoj ovládací prvky typu virtuální seznam. Další informace najdete v části problémy s kompatibilitou tématu ovládací prvky zobrazení seznamu ve Windows SDK.  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>Zpracování oznámení LVN_GETDISPINFO  
 Ovládací prvky typu virtuální seznam Udržovat velmi málo informací položky. S výjimkou výběr položek a informace fokus všechny informace o položce spravuje vlastník ovládacího prvku. Informace se požaduje rámcem prostřednictvím **LVN_GETDISPINFO** oznámení. Pokud chcete zadat požadované informace, musí vlastník ovládacího prvku virtuální seznam (nebo samotném ovládacím prvku) zpracovat toto oznámení. To můžete snadno provést pomocí okna vlastnosti (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)). Výsledný kód by měl vypadat podobně jako v následujícím příkladu (kde `CMyDialog` vlastní objekt ovládacího prvku seznam virtuálních a dialogové okno zpracovává oznámení):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 V obslužné rutině **LVN_GETDISPINFO** oznámení, musíte zkontrolovat, v tématu, jaké typy informací je požadováno. Možné hodnoty jsou:  
  
-   `LVIF_TEXT``pszText` Člena musí být vyplněna.  
  
-   `LVIF_IMAGE``iImage` Člena musí být vyplněna.  
  
-   **LVIF_INDENT** *iIndent* člena musí být vyplněna.  
  
-   `LVIF_PARAM`*LParam* člena musí být vyplněna. (Není k dispozici pro dílčí položky.)  
  
-   `LVIF_STATE`*Stavu* člena musí být vyplněna.  
  
 Potom, zadejte libovolnou informace se požaduje zpět na rozhraní.  
  
 Následující příklad (převzata z textu oznámení obslužné rutiny pro objekt ovládacího prvku seznam) ukazuje jedna z možných metod zadáním informace pro textové vyrovnávací paměti a bitové kopie položky:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>Ukládání do mezipaměti a virtuální ovládací prvky seznamu  
 Protože tento typ ovládacího prvku seznam je určený pro velké sady dat, doporučuje se, že je požadovaná položka ukládat data do mezipaměti ke zlepšení výkonu načtení. Rozhraní framework poskytuje mechanismus zobrazování rad mezipaměti jako pomůcku při optimalizaci mezipaměti odesláním **LVN_ODCACHEHINT** oznámení.  
  
 Následující příklad aktualizuje mezipaměť s rozsahem předaný funkci obslužné rutiny.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 Další informace o přípravě a údržbu mezipaměti najdete v části Správa mezipaměti tématu ovládací prvky zobrazení seznamu ve Windows SDK.  
  
## <a name="finding-specific-items"></a>Hledání konkrétní položky  
 **LVN_ODFINDITEM** odešle oznámení ovládacího prvku seznam virtuálních v případě, že dané položky řízení musí být nalezen. Odeslání zprávy oznámení ovládacího prvku zobrazení seznamu přijetí rychlý přístup ke klíčům nebo, pokud obdrží **LVM_FINDITEM** zprávy. Hledání informace se odesílají ve formě **LVFINDINFO** struktura, který je členem z **NMLVFINDITEM** struktury. Zpracování této zprávy přepsáním `OnChildNotify` funkce seznamu řízení objektu a do těla obslužné rutiny, vyhledejte **LVN_ODFINDITEM** zprávy. Pokud nalezen, proveďte příslušnou akci.  
  
 Měli byste být připravení vyhledejte položku, která odpovídá informace poskytují ovládacího prvku zobrazení seznamu. Index položky v případě úspěchu nebo -1 by měl vrátit, pokud se nenajde žádné odpovídající položky.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CListCtrl](../mfc/using-clistctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

