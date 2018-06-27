---
title: Kdy jsou volány obslužné rutiny aktualizace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c033d33dd6b1e6c0ccd5bbdb4b6af6939521f592
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956171"
---
# <a name="when-update-handlers-are-called"></a>Kdy jsou volány obslužné rutiny aktualizace
Předpokládejme, že uživatel klikne na tlačítko myši v nabídce Soubor, který generuje WM_INITMENUPOPUP zprávu. V rámci aktualizace Frameworku souhrnně aktualizuje všechny položky v nabídce soubor před rozbalení nabídky, takže uživatel uvidí.  
  
 K tomuto účelu trasy framework aktualizovat příkazy pro všechny položky nabídky v rozbalovací nabídce podél standardního směrování příkazů. Cíle příkazů na směrování je moci aktualizovat všechny položky nabídky porovnáním příkaz aktualizace se záznamem příslušné mapy zpráv (ve formátu `ON_UPDATE_COMMAND_UI`) a volání funkce "Obslužná rutina aktualizace". Proto nabídky se šesti položky nabídky, šesti příkazy aktualizace jsou odeslána. Pokud obslužnou rutinu aktualizace existuje pro ID příkazu, který položky nabídky, se nazývá provedete aktualizaci. Pokud ne, zkontroluje existenci obslužná rutina pro tento příkaz ID rozhraní a povolí nebo zakáže položku nabídky podle potřeby.  
  
 Pokud nenajde rozhraní `ON_UPDATE_COMMAND_UI` položka během směrování příkazů automaticky umožňuje objekt uživatelského rozhraní Pokud dojde `ON_COMMAND` položka někde se stejným ID příkazu. V opačném zakáže objekt uživatelského rozhraní. Proto zkontrolujte, zda je povoleno objekt uživatelského rozhraní, zadejte obslužnou rutinu pro příkaz, který generuje objekt nebo zadat obslužnou rutinu aktualizace. Podívejte se na obrázek v tomto tématu [identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md).  
  
 Je možné zakázat výchozí zakázání objektů uživatelského rozhraní. Další informace najdete v tématu [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) člena třídy `CFrameWnd` v *odkaz knihovny MFC*.  
  
 Inicializace nabídky je automaticky v rámci, ke kterým dochází, když aplikace přijme zprávu o WM_INITMENUPOPUP. Během nečinné smyčky framework prohledává příkaz směrování pro obslužné rutiny aktualizace tlačítko mnohem stejným způsobem jako v případě nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

