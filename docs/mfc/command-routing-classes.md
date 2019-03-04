---
title: Třídy směrování příkazů
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: 264e931ba0468cdc44f27c55e5d259948c5392b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281966"
---
# <a name="command-routing-classes"></a>Třídy směrování příkazů

Během interakce uživatele s aplikací výběrem nabídky nebo tlačítka ovládacích panelů pomocí myši aplikace odesílá zprávy z objektu ovlivněné uživatelského rozhraní na odpovídající objekt cíli příkazu. Cíl příkazu třídy odvozené z `CCmdTarget` zahrnují [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), a z nich odvozené třídy. Rozhraní framework podporuje automatické příkaz směrování tak, aby příkazy mohou být zpracovány v aplikaci aktuálně aktivní nejvhodnější objektu.

Objekt třídy `CCmdUI` je předán příkazu pro aktualizaci cíle příkazů uživatelského rozhraní ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) obslužných rutin, aby bylo možné aktualizovat stav uživatelského rozhraní pro ke konkrétnímu příkazu (například pro kontrolu nebo odebrat Kontrola z položek nabídky). Volat členské funkce `CCmdUI` objektu k aktualizaci stavu objektů uživatelského rozhraní. Tento proces je stejný, zda je objekt uživatelského rozhraní, které jsou přidružené ke konkrétnímu příkazu. položka nabídky nebo tlačítko nebo obojí.

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
Slouží jako základní třída pro všechny třídy objektů, které může přijímat a reagovat na zprávy.

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
Poskytuje programové rozhraní pro aktualizace objektů uživatelského rozhraní, jako je například položky nabídky nebo tlačítka ovládacích panelů. Cílový objekt příkazu umožňuje, zakáže, zkontroluje nebo vymaže objekt uživatelského rozhraní s tímto objektem.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
