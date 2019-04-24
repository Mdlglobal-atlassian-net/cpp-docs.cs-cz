---
title: Mapování zpráv na funkce
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 7ed2b66ffe382cc8683b811362fb014597168037
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321972"
---
# <a name="mapping-messages-to-functions"></a>Mapování zpráv na funkce

V okně Vlastnosti umožňuje vytvořit vazbu obslužné rutiny zpráv (členské funkce tříd knihovny MFC uživatelského rozhraní) zprávy vygenerovaných vašimi prostředky vaší aplikace. Používají [mapy zpráv knihovny MFC](../../mfc/messages-and-commands-in-the-framework.md) pro vytvoření vazby.

Použijete-li vytvořit novou třídu odvozenou z jedné třídy rámec zobrazení tříd, je automaticky umístí úplné a funkční třídy v záhlaví (.h) a implementaci (.cpp) soubory, které zadáte.

> [!NOTE]
>  Chcete-li přidat novou třídu, která nezpracovává zprávy, vytvořte třídu přímo v textovém editoru.

### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Definování nebo odebrání obslužné rutiny zpráv pomocí okna Vlastnosti

1. V zobrazení tříd klikněte na třídu.

1. V okně Vlastnosti klikněte na tlačítko **zprávy** tlačítko.

    > [!NOTE]
    >  **Zprávy** tlačítko je k dispozici při výběru názvu třídy v zobrazení tříd nebo když kliknete na okno zdrojového kódu.

   Pokud váš projekt obsahuje obslužné rutiny pro zprávy, název obslužné rutiny zobrazí v pravém sloupci vedle zprávy.

1. Pokud zpráva nemá žádná obslužná rutina, pak klikněte na buňku v pravém sloupci v okně Vlastnosti, chcete-li zobrazit navrhovaný název obslužné rutiny jako \<Přidat >*HandlerName*. (Například obslužná rutina zprávy WM_TIMER navrhuje \<Přidat >`OnTimer`).

1. Kliknutím na navrhovaný název přidat kód zástupných procedur pro funkci.

1. Úpravy obslužné rutiny zpráv, dvakrát klikněte na zprávu v zobrazení tříd a úpravy kódu v okně zdroje.

K odebrání obslužné rutiny zpráv, klikněte dvakrát na obslužnou rutinu v pravém sloupci a vyberte \<odstranit >*HandlerName*. Je zakomentovaný, kód vaší funkce.

## <a name="see-also"></a>Viz také:

[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Přidání obslužných rutin události pro ovládací prvky dialogového okna](../../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
