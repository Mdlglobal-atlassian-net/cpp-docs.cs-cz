---
title: "Průvodce obslužnou rutinou události | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords: Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f2f871381f64627caa76c28c5195143e1b391f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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