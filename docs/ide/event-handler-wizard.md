---
title: Průvodce obslužnou rutinou události | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 544ce4cd0f4ed9a7f3592e5ec1691fb3734b8772
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33340005"
---
# <a name="event-handler-wizard"></a>Průvodce obslužnou rutinou události
Tento průvodce přidá obslužné rutiny události pro ovládací prvek dialogového okna pro třídu podle svého výběru. Pokud přidáte obslužné rutiny události z [vlastnosti – okno](/visualstudio/ide/reference/properties-window), můžete ho přidat pouze pro třídu, která implementuje dialogové okno. V tématu [přidání obslužné rutiny události pro ovládací prvky dialogové okno](../windows/adding-event-handlers-for-dialog-box-controls.md) Další informace.  
  
 **Název příkazu**  
 Určuje vybraný ovládací prvek, pro kterou je obslužná rutina přidána. Toto pole je k dispozici.  
  
 **Typ zprávy**  
 Zobrazí seznam aktuální obslužné rutiny zpráv možné pro vybraný ovládací prvek.  
  
 **Název obslužné rutiny – funkce**  
 Zobrazuje název funkce, která je přičtena ke zpracování události. Ve výchozím nastavení je název podle typu zprávy a příkaz přidá jako předpona podle "Na". Například pro tlačítko názvem `IDC_BUTTON1`, typ zprávy `BN_CLICKED` zobrazí název obslužné rutiny funkce `OnBnClickedButton1`.  
  
 **Třídy seznamu**  
 Zobrazí dostupné třídy, na které můžete přidat obslužné rutiny události. Třída pro dialogové okno vybrané se zobrazí červeně.  
  
 **Popis obslužné rutiny**  
 Obsahuje popis pro vybranou položku v **typ zprávy** pole. Toto pole je k dispozici.  
  
 **Přidávání a úprava**  
 Přidá popisovač zpráv pro vybranou třídu nebo objekt a následně otevírá textovém editoru a nové funkce, můžete přidat kód pro obslužnou rutinu oznámení ovládacího prvku.  
  
 **Úpravy kódu**  
 Otevře textového editoru na vybrané existující funkce, které můžete přidat nebo upravit kód obslužné rutiny oznámení ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Přidání obslužné rutiny událostí](../ide/adding-an-event-handler-visual-cpp.md)