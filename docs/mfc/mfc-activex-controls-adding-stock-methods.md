---
title: "Ovládací prvky MFC ActiveX: Přidání uložených metod | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a517362ebb4d439394197234eaa51a5aef7f5940
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC – ovládací prvky ActiveX: Přidání uložených metod
Uložené metody se liší od vlastní metoda v tom, že už je implementováno třídou [COleControl](../mfc/reference/colecontrol-class.md). Například `COleControl` obsahuje člen předdefinované funkci, která podporuje metodu aktualizace pro ovládací prvek. Položka mapy odeslání pro tuto metodu uložených je **DISP_STOCKFUNC_REFRESH**.  
  
 `COleControl`podporuje dvě metody uložených: DoClick – a aktualizace. Aktualizace je volána uživatelem ovládacího prvku okamžitě aktualizovat vzhled ovládacího prvku; DoClick – vyvolání má provést, klikněte na tlačítko ovládacího prvku událost.  
  
|Metoda|Položku mapy odesílání|Komentář|  
|------------|------------------------|-------------|  
|`DoClick`|**(DISP_STOCKPROP_DOCLICK)**|Aktivuje událost klikněte na tlačítko.|  
|**Aktualizace**|**(DISP_STOCKPROP_REFRESH)**|Okamžitě aktualizuje vzhledu ovládacího prvku.|  
  
##  <a name="_core_adding_a_stock_method_using_classwizard"></a>Přidání uložených metoda pomocí Průvodce přidáním metody  
 Přidání uložené metody je jednoduchá pomocí [Průvodce přidáním metody](../ide/add-method-wizard.md). Následující postup předvádí, přidání do ovládacího prvku vytvořené pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC metoda obnovení.  
  
#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>Chcete-li přidat uložených metoda obnovení pomocí Průvodce přidáním metody  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat metodu**.  
  
     Otevře se Průvodce přidáním metody.  
  
5.  V **název metody** pole, klikněte na tlačítko **aktualizovat**.  
  
6.  Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_stock_methods"></a>Přidání metoda průvodce změní pro uložených metod  
 Protože uložených metoda aktualizace je podporována základní třídou ovládacího prvku **Průvodce přidáním metody** deklaraci třídy ovládacího prvku nijak nemění. Přidá položku pro metodu expediční mapy ovládacího prvku a jeho. IDL soubor. Následující řádek je přidán do ovládacího prvku expediční mapy, umístěný v jeho implementaci (. Soubor CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]  
  
 Díky metoda obnovení k dispozici uživatelům ovládacího prvku.  
  
 Následující řádek je přidán do ovládacího prvku. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]  
  
 Tento řádek přiřadí způsob aktualizace na konkrétní číslo ID.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)

