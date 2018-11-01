---
title: ON_UPDATE_COMMAND_UI – makro
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: d0487f6a69d144e46adab496f3fd21696b5b434b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594101"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI – makro

Použití **vlastnosti** okno pro připojení objektu uživatelského rozhraní pro obslužnou rutinu aktualizace příkazů v příkazu cílový objekt. Bude automaticky připojit ID objektu uživatelské rozhraní ON_UPDATE_COMMAND_UI – makro a vytvořte obslužnou rutinu v objektu, který bude zpracovávat aktualizace. Zobrazit [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md) Další informace.

Například pokud chcete vymazat všechny příkaz v nabídce Úpravy váš program aktualizovat, použijte **vlastnosti** se okno Přidat položku mapování zpráv ve třídě zvolené deklaraci funkce obslužné rutiny aktualizace příkazů `OnUpdateEditClearAll` ve třídě deklarace a šablonu funkce empty v souboru implementace třídy. Prototyp funkce vypadá takto:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Všechny obslužné rutiny, zobrazí se funkce, jako jsou **afx_msg** – klíčové slovo. Stejně jako všechny obslužné rutiny aktualizace, přijímá jeden argument, ukazatel `CCmdUI` objektu.

## <a name="see-also"></a>Viz také

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)

