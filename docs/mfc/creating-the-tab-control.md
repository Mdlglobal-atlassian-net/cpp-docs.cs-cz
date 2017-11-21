---
title: "Vytvoření ovládacího prvku karta | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs: C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db477a8966e7a7ec5368e5ed9e783b466acbf103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-the-tab-control"></a>Vytvoření ovládacího prvku karta
Vytvoření ovládacího prvku karta závisí na tom, jestli jsou pomocí ovládacího prvku v dialogovém okně nebo jeho vytváření v okně nondialog.  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>K použití přímo v dialogovém okně CTabCtrl  
  
1.  V editoru dialogového okna přidáte do šablony zdroje dialogové okno ovládacího prvku karta. Zadejte své ID ovládacího prvku.  
  
2.  Použití [Průvodce přidáním členské proměnné](../ide/adding-a-member-variable-visual-cpp.md) přidání členské proměnné typu [CTabCtrl](../mfc/reference/ctabctrl-class.md) s vlastností ovládacího prvku. Tento člen mohou využít k volání `CTabCtrl` členské funkce.  
  
3.  Mapování funkce obslužných rutin ve třídě dialog pro všechny zpráv oznámení ovládacího prvku karta, které je třeba zpracovat. Další informace najdete v tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md).  
  
4.  V [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), nastavení stylů pro `CTabCtrl`.  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>V okně nondialog používat CTabCtrl  
  
1.  Definování ovládacího prvku ve třídě zobrazení nebo okno.  
  
2.  Volání ovládacího prvku [vytvořit](../mfc/reference/ctabctrl-class.md#create) člen funkce, které by mohly mít v [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), pravděpodobně časná jako nadřazeného okna [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkce obslužné rutiny (Pokud jste vytvoření podtřídy ovládacího prvku). Nastavení stylů pro ovládací prvek.  
  
 Po `CTabCtrl` objekt byl vytvořen, můžete nastavit nebo vymazat následující rozšířené styly:  
  
-   **Tcs_ex_flatseparators –** ovládacího prvku karta bude kreslení oddělovačů mezi položkami kartě. Rozšířený styl jen ovlivňuje kartě ovládací prvky, které mají **TCS_BUTTONS** a **TCS_FLATBUTTONS** stylů. Ve výchozím nastavení, vytvoření ovládacího prvku karta s **TCS_FLATBUTTONS** styl nastaví tento rozšířený styl.  
  
-   **Tcs_ex_registerdrop –** generuje ovládacího prvku karta **TCN_GETOBJECT** zpráv s oznámením o cíle přetažení objektu při přetažení objektu přes Karta položky v ovládacím prvku.  
  
    > [!NOTE]
    >  Pro příjem **TCN_GETOBJECT** oznámení, je třeba inicializovat knihoven OLE pomocí volání [AfxOLEInit –](../mfc/reference/ole-initialization.md#afxoleinit).  
  
 Tyto styly můžete načíst a nastavit po vytvoření ovládacího prvku pomocí příslušných volání [GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) a [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) členské funkce.  
  
 Například nastavit **tcs_ex_flatseparators –** styl s následujícími řádky kódu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 Vymazat **tcs_ex_flatseparators –** styl z `CTabCtrl` objekt s následující řádky kódu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 Tato akce odebere oddělovačů, které se zobrazují mezi tlačítky z vaší `CTabCtrl` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CTabCtrl](../mfc/using-ctabctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

