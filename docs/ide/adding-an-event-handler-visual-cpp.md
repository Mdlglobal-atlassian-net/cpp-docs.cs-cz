---
title: "Přidání obslužné rutiny události (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9a5380bf335a13bbf7b2f54840c9d1160187167
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-event-handler-visual-c"></a>Přidání obslužné rutiny události (Visual C++)
V editoru prostředků, můžete přidat novou obslužnou rutinu události nebo upravovat stávající obslužné rutiny události pro dialogové okno pole ovládacího prvku pomocí [Průvodce obslužnou rutinou události](../ide/event-handler-wizard.md).  
  
 Událost můžete přidat do třídy implementující dialogové okno pole pomocí [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Pokud chcete přidat událost na třídu než třídy dialogového okna, použijte Průvodce obslužnou rutinou události.  
  
### <a name="to-add-an-event-handler-to-a-dialog-box-control"></a>Přidání obslužné rutiny události pro ovládací prvek dialogového okna  
  
1.  Dvakrát klikněte na pole prostředku dialogového okna v [zobrazení prostředků](../windows/resource-view-window.md) otevřete dialogové okno pole prostředek, který obsahuje ovládacího prvku [editoru dialogového okna](../windows/dialog-editor.md).  
  
2.  Klikněte pravým tlačítkem na ovládací prvek, pro které chcete ke zpracování události oznámení.  
  
3.  V místní nabídce klikněte na tlačítko **přidejte obslužné rutiny události** zobrazíte Průvodce obslužnou rutinou události.  
  
4.  Vyberte události v **typ zprávy** políčko k přidání ke třídě vybrané v **seznam tříd** pole.  
  
5.  Přijměte výchozí název **název obslužné rutiny funkce** pole, nebo zadejte název svého výběru.  
  
6.  Klikněte na tlačítko **přidat a upravit** přidejte obslužné rutiny události do projektu a otevřete textový editor v nové funkce přidat kód pro obslužnou rutinu události.  
  
     Pokud je typ vybrané zprávy již obslužné rutiny události pro vybrané třídy **přidat a upravit** není k dispozici, a **upravit kód** je k dispozici. Klikněte na tlačítko **upravit kód** otevřete textový editor v stávající funkce.  
  
 Alternativně můžete přidat obslužné rutiny událostí z [vlastnosti – okno](/visualstudio/ide/reference/properties-window). V tématu [přidání obslužné rutiny události pro ovládací prvky dialogové okno](../windows/adding-event-handlers-for-dialog-box-controls.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)   
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)