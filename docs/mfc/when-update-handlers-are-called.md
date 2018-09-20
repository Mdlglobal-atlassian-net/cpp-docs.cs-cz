---
title: Kdy jsou volány obslužné rutiny aktualizace | Dokumentace Microsoftu
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
ms.openlocfilehash: 462bdb99c4f17232405db9df8e5bcb0da9861b69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397751"
---
# <a name="when-update-handlers-are-called"></a>Kdy jsou volány obslužné rutiny aktualizace

Předpokládejme, že uživatel klikne myší v nabídce Soubor, který generuje WM_INITMENUPOPUP zprávy. V rámci aktualizace Frameworku souhrnně aktualizuje všechny položky v nabídce soubor před rozbalení nabídky, takže ji vidí uživatel.

K tomuto účelu aktualizovat trasy framework příkazy pro všechny položky nabídky v rozbalovací nabídce podél standardního směrování příkazů. Cíle příkazů na směrování mít příležitost k aktualizaci všechny položky nabídky to provede spárováním odpovídajících příkazu update s položkou odpovídající map zpráv (ve formátu `ON_UPDATE_COMMAND_UI`) a volání funkce "Obslužná rutina aktualizace". Díky tomu se pro nabídky s šest položek nabídky, šesti příkazů update odeslání. Pokud obslužnou rutinu aktualizace existuje pro Identifikátor příkazu položky nabídky, se nazývá provedete aktualizaci. Pokud ne, rozhraní zkontroluje existenci obslužnou rutinu pro toto ID příkazu a povolí nebo zakáže položky nabídky podle potřeby.

Pokud nelze najít rozhraní `ON_UPDATE_COMMAND_UI` položka během směrování příkazů, automaticky umožňuje objekt uživatelského rozhraní dojde `ON_COMMAND` položka někde se stejným ID příkazu. V opačném případě zakáže objekt uživatelského rozhraní. Proto ujistěte se, že je povoleno objekt uživatelského rozhraní, zadejte obslužnou rutinu pro příkaz, který generuje objekt nebo zadejte pro něj obslužné rutiny aktualizace. Podívejte se na obrázek v tomto tématu [identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md).

Je možné zakázat výchozí zakázání objektů uživatelského rozhraní. Další informace najdete v tématu [m_bAutoMenuEnable](../mfc/reference/cframewnd-class.md#m_bautomenuenable) člena třídy `CFrameWnd` v *odkaz knihovny MFC*.

Inicializace nabídce je v rozhraní, ke kterým dochází, když aplikace obdrží zprávu WM_INITMENUPOPUP automatické. Během nečinné smyčky framework prohledává příkaz směrování pro obslužné rutiny aktualizace tlačítko v podstatě stejným způsobem jako u nabídek.

## <a name="see-also"></a>Viz také

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

