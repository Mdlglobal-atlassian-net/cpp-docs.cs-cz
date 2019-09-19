---
title: ON_UPDATE_COMMAND_UI – makro
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 2a3f097a44e96fc470719ce636cc1b73e676fb38
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095838"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI – makro

Chcete-li připojit objekt uživatelského rozhraní k obslužné rutině aktualizace příkazu v objektu Target příkazu, otevřete **zobrazení tříd**, klikněte pravým tlačítkem na třídu, do které bude obslužná rutina přidána, a zvolte možnost **Průvodce třídou**. V seznamu na levé straně Najděte ID objektu uživatelského rozhraní a v pravém podokně zvolte **UPDATE_COMMAND_UI** a klikněte na **Přidat obslužnou rutinu**. Tím se ve třídě vytvoří funkce obslužné rutiny a přidá odpovídající položku v mapě zpráv. Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md) . V podokně **zprávy** můžete určit další zprávy, které se mají zpracovat.

Například chcete-li aktualizovat příkaz Zrušit vše v nabídce úprav programu, použijte **Průvodce třídou** k přidání položky mapování zpráv do vybrané třídy, deklarace funkce pro obslužnou rutinu aktualizace příkazu volanou `OnUpdateEditClearAll` v deklaraci třídy a prázdné Šablona funkce v implementačním souboru třídy Prototyp funkce vypadá takto:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Podobně jako všechny obslužné rutiny, deklarace funkce zobrazuje klíčové slovo **afx_msg** . Stejně jako všechny obslužné rutiny aktualizace přebírá jeden argument, ukazatel na `CCmdUI` objekt.

## <a name="see-also"></a>Viz také:

[Postupy: Aktualizace objektů uživatelského rozhraní](../mfc/how-to-update-user-interface-objects.md)
