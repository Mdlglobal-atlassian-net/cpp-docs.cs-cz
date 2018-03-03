---
title: "Přidání záznamu do tabulky akcelerátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fe2df81aae0b9b7232443de1db091a9cbb0c0d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>Přidání záznamu do tabulky akcelerátorů
### <a name="to-add-an-entry-to-an-accelerator-table"></a>Přidání záznamu do tabulky akcelerátorů  
  
1.  Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem do tabulky akcelerátorů a zvolte **nový akcelerátor** z místní nabídky, nebo klikněte na položku prázdný řádek v dolní části tabulky.  
  
3.  Vyberte [ID](id-property.md) z rozevíracího seznamu v ID pole nebo zadejte nové ID v **ID** pole.  
  
4.  Typ [klíč](../windows/accelerator-key-property.md) chcete použít jako akcelerátoru nebo klikněte pravým tlačítkem a zvolte **další zadali klíč** z místní nabídky k nastavení kombinace kláves ( **další zadali klíč** příkaz je je dostupný také z **upravit** nabídky).  
  
5.  Změna [modifikátor](../windows/accelerator-modifier-property.md) a [typu](../windows/accelerator-type-property.md), v případě potřeby.  
  
6.  Stiskněte klávesu **ENTER**.  
  
    > [!NOTE]
    >  Ujistěte se, že všechny akcelerátorů, které definujete jsou jedinečné. Může mít několik kombinace kláves přiřazené stejné ID s neplatí chybný, například CTRL + P a F8 můžete obě přiřadit ke ID_PRINT. Však s kombinaci kláves přiřadit více než jeden, který ID nebude fungovat správně, například CTRL + Z přiřazeného k ID_SPELL_CHECK a ID_THESAURUS.  
  

  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)