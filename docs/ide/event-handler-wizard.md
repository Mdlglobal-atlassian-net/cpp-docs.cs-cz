---
title: Průvodce obslužnou rutinou události
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
ms.openlocfilehash: e48d995aed0c59cc4ba7b645706448b5c3618b4a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654165"
---
# <a name="event-handler-wizard"></a>Průvodce obslužnou rutinou události

Tento průvodce přidá do vámi vybrané třídy obslužnou rutinu události pro ovládací prvek dialogového okna. Pokud chcete přidat obslužnou rutinu události z [okno vlastností](/visualstudio/ide/reference/properties-window), ho můžete přidat pouze do třídy, která implementuje dialogových oken. Zobrazit [přidání obslužné rutiny události pro ovládací prvky dialogového okna](../windows/adding-event-handlers-for-dialog-box-controls.md) Další informace.

- **Název příkazu**

   Určuje vybraný ovládací prvek, pro který se přidá obslužnou rutinu události. Toto pole je k dispozici.

- **Typ zprávy**

   Zobrazí seznam aktuální obslužné rutiny zpráv možné pro vybraný ovládací prvek.

- **Název obslužné rutiny – funkce**

   Zobrazuje název funkce, která se přidá ke zpracování události. Ve výchozím nastavení je název podle typu zprávy a příkaz předcházený "Na". Například pro tlačítko názvem `IDC_BUTTON1`, typ zprávy `BN_CLICKED` zobrazí název obslužné rutiny funkce `OnBnClickedButton1`.

- **Seznam tříd**

   Zobrazí dostupné třídy, na které můžete přidat obslužnou rutinu události. Třída pro vybrané dialogové okno se zobrazí červeně.

- **Popis obslužné rutiny**

   Poskytuje popis položky vybrané v **typ zprávy** pole. Toto pole je k dispozici.

- **Přidávání a úprava**

   Přidá popisovač zprávy pro vybranou třídu nebo objektu a následně otevírá textového editoru na tuto novou funkci, můžete přidat kód pro obslužnou rutinu oznámení ovládacího prvku.

- **Úpravy kódu**

   Proto můžete přidat nebo upravit kód pro obslužnou rutinu oznámení ovládací prvek, otevře se textovém editoru na vybrané existující funkce.

## <a name="see-also"></a>Viz také

[Přidání obslužné rutiny událostí](../ide/adding-an-event-handler-visual-cpp.md)