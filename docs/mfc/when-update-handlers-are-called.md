---
title: "Kdy jsou volány obslužné rutiny aktualizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- updating user interface objects [MFC]
- command routing [MFC], update commands
- toolbar buttons [MFC], enabling
- disabling toolbar buttons
- menus [MFC], initializing
- update handlers [MFC]
- disabling menu items
- toolbars [MFC], updating
- menus [MFC], updating as context changes
- toolbar controls [MFC], updated during OnIdle method [MFC]
- menu items, enabling
- command routing [MFC], update handlers
- update handlers, calling
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b19a01ce06b76b49593adf54fa8af728be2d5c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="when-update-handlers-are-called"></a>Kdy jsou volány obslužné rutiny aktualizace
Předpokládejme, že uživatel klikne na tlačítko myši v nabídce Soubor, který generuje `WM_INITMENUPOPUP` zprávy. V rámci aktualizace Frameworku souhrnně aktualizuje všechny položky v nabídce soubor před rozbalení nabídky, takže uživatel uvidí.  
  
 K tomuto účelu trasy framework aktualizovat příkazy pro všechny položky nabídky v rozbalovací nabídce podél standardního směrování příkazů. Cíle příkazů na směrování je moci aktualizovat všechny položky nabídky porovnáním příkaz aktualizace se záznamem příslušné mapy zpráv (ve formátu `ON_UPDATE_COMMAND_UI`) a volání funkce "Obslužná rutina aktualizace". Proto nabídky se šesti položky nabídky, šesti příkazy aktualizace jsou odeslána. Pokud obslužnou rutinu aktualizace existuje pro ID příkazu, který položky nabídky, se nazývá provedete aktualizaci. Pokud ne, zkontroluje existenci obslužná rutina pro tento příkaz ID rozhraní a povolí nebo zakáže položku nabídky podle potřeby.  
  
 Pokud nenajde rozhraní `ON_UPDATE_COMMAND_UI` položka během směrování příkazů automaticky umožňuje objekt uživatelského rozhraní Pokud dojde `ON_COMMAND` položka někde se stejným ID příkazu. V opačném zakáže objekt uživatelského rozhraní. Proto zkontrolujte, zda je povoleno objekt uživatelského rozhraní, zadejte obslužnou rutinu pro příkaz, který generuje objekt nebo zadat obslužnou rutinu aktualizace. Podívejte se na obrázek v tomto tématu [identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md).  
  
 Je možné zakázat výchozí zakázání objektů uživatelského rozhraní. Další informace najdete v tématu [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) člena třídy `CFrameWnd` v *odkaz knihovny MFC*.  
  
 Inicializace nabídky je automatické v rozhraní framework, ke kterým dochází, když obdrží aplikace `WM_INITMENUPOPUP` zprávy. Během nečinné smyčky framework prohledává příkaz směrování pro obslužné rutiny aktualizace tlačítko mnohem stejným způsobem jako v případě nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)
