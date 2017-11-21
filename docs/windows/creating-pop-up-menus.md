---
title: "Vytváření místních nabídek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 529e0b4a659a3ea0c879db2c3b2a3bd4a9a3d160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-pop-up-menus"></a>Vytváření místních nabídek
[Místní nabídky](../mfc/menus-mfc.md) zobrazení často používané příkazy. Může se jednat kontextově závislá na umístění ukazatele. Pomocí místní nabídky v aplikaci vyžaduje vytváření nabídky sám a následným připojením ke kódu aplikace.  
  
 Po vytvoření prostředků nabídky kódu aplikace musí načíst zdroj nabídky a použít [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) způsobí v nabídce Zobrazit. Jakmile uživatel má vynechat v místní nabídce kliknete na mimo něj, nebo klepnutí na příkaz, že funkce vrátí. Pokud uživatel vybere příkaz, odešle příkaz zprávy do okna byl předán jejichž popisovač.  
  
### <a name="to-create-a-pop-up-menu"></a>Chcete-li vytvořit místní nabídky  
  
1.  [Vytvořit nabídku](../windows/creating-a-menu.md) s prázdný název (neposkytují **popisek**).  
  
2.  [Příkaz nabídky přidat do nové nabídky](../windows/adding-commands-to-a-menu.md). Přesuňte do první příkaz nabídky pod ním prázdné nabídky (titulek dočasné textem sem typ). Zadejte **popisek** a všechny ostatní informace.  
  
     Tento postup opakujte pro všechny ostatní příkazy nabídky v místní nabídce.  
  
3.  Uložte prostředků nabídky.  
  
    > [!TIP]
    >  Další informace o zobrazení v místní nabídce najdete v tématu [zobrazení nabídky jako místní nabídky](../windows/viewing-a-menu-as-a-pop-up-menu.md).  
  

  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Připojení místní nabídky do vaší aplikace](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Editor nabídek](../windows/menu-editor.md)