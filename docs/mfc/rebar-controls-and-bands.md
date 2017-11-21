---
title: "Matrice – ovládací prvky a pruhy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc9e78f38f911feac117023fc46b9c15d43e9128
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rebar-controls-and-bands"></a>Matrice – ovládací prvky a pruhy
Hlavním účelem ovládacím prvkem matrice je tak, aby fungoval jako kontejner pro podřízená okna, běžné ovládací prvky dialogového okna, nabídek, panely nástrojů a tak dále. Toto omezení je podporován koncepci "vzdálené". Každé vzdálené matrice může obsahovat libovolnou kombinaci úchytu panelu, rastrový obrázek, text popisku a podřízeného okna.  
  
 Třída `CReBarCtrl` má mnoho členské funkce, můžete použít k načtení a upravit informace o konkrétní matrice pásmo:  
  
-   [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) načte počet aktuální pruhy v ovládacím prvku matrice.  
  
-   [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) inicializuje **REBARBANDINFO** struktura informacemi ze zadané vzdálené správy. Neexistuje odpovídající [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) – členská funkce.  
  
-   [GetRect –](../mfc/reference/crebarctrl-class.md#getrect) načte ohraničující obdélník zadaný vzdálené správy.  
  
-   [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) načte počet vzdálené řádků v ovládacím prvku matrice.  
  
-   [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) načte index zadaný vzdálené správy.  
  
-   [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) načte ohraničení pásmo.  
  
 Kromě manipulaci několik členské funkce jsou k dispozici, které umožňují pracovat pruhy matrice konkrétní.  
  
 [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) a [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) přidávat a odebírat pruhy matrice. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) a [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) ovlivnit aktuální velikost konkrétní matrice vzdálené. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) změny index konkrétní matrice vzdálené. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) zobrazí nebo skryje matrice vzdálené od uživatele.  
  
 Následující příklad ukazuje, přidání panelu nástrojů (`m_wndToolBar`) do existujícího ovládacího prvku matrice (`m_wndReBar`). Vzdálené správy je popsán inicializace `rbi` strukturu a pak volání `InsertBand` – členská funkce:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

