---
title: Mapování zpráv na funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b53175e46cfa858a73b581dfefc78047e96380d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058946"
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

## <a name="see-also"></a>Viz také

[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Přidání obslužných rutin události pro ovládací prvky dialogového okna](../../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
