---
title: "Implementace dialogové okno | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CSimpleDialog class, implementing dialog boxes in ATL
- dialog boxes, ATL
- CAxDialogImpl class, implementing dialog boxes in ATL
- ATL, dialog boxes
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e4a8f0d4ef6e8f5ea73352f0d4a62acee1c8c89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-dialog-box"></a>Implementace dialogové okno
Existují dva způsoby, jak dialogové okno Přidat do projektu knihovny ATL: použijte dialogové okno průvodce ATL nebo je přidat ručně.  
  
## <a name="adding-a-dialog-box-with-the-atl-dialog-wizard"></a>Přidání dialogového okna pomocí Průvodce dialogové okno knihovny ATL  
 V [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md), vyberte objekt ATL dialogové okno pro přidání do projektu knihovny ATL dialogové okno. Vyplňte dialogové okno průvodce ATL podle potřeby a klikněte na tlačítko **Dokončit**. Průvodce přidá třídy odvozené od [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) do projektu. Otevření zobrazení prostředků z **zobrazení** nabídce najít do dialogu a dvojím kliknutím otevřete v editoru prostředků.  
  
> [!NOTE]
>  Pokud vaše dialogové okno je odvozený od `CAxDialogImpl`, může být hostitelem obou ActiveX a ovládací prvky systému Windows. Pokud nechcete, aby nároky na podporu ovládacích prvků ActiveX v vaší třídy dialogového okna, použijte [CSimpleDialog](../atl/reference/csimpledialog-class.md) nebo [CDialogImpl](../atl/reference/cdialogimpl-class.md) místo.  
  
 Obslužné rutiny zpráv a událostí můžete přidat do vlastní třídy dialogového okna v zobrazení tříd. Další informace najdete v tématu [Přidání popisovače zpráv knihovny ATL](../atl/adding-an-atl-message-handler.md).  
  
## <a name="adding-a-dialog-box-manually"></a>Ruční přidání dialogového okna  
 Implementace dialogového okna je podobná implementace časového období. Odvození třídy z buď [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md), [CDialogImpl](../atl/reference/cdialogimpl-class.md), nebo [CSimpleDialog](../atl/reference/csimpledialog-class.md) a deklarovat [mapy zpráv](../atl/message-maps-atl.md) pro zpracování zprávy. Identifikátor prostředku šablony dialogového okna však nutné také zadat v odvozené třídě. Třídu musí mít data člena s názvem `IDD` pro tuto hodnotu.  
  
> [!NOTE]
>  Když vytvoříte dialogového okna pomocí knihovny ATL dialogové okno průvodce, průvodce automaticky přidá `IDD` členem, jako `enum` typu.  
  
 `CDialogImpl`umožňuje implementovat modální nebo nemodální dialogové okno, který je hostitelem ovládací prvky systému Windows. `CAxDialogImpl`umožňuje implementovat modální nebo nemodální dialogové okno, který je hostitelem ovládací prvky ActiveX a systému Windows.  
  
 Modální dialogové okno vytvořit, vytvořit instanci vaší `CDialogImpl`-odvozené (nebo `CAxDialogImpl`-odvozené) třídy a pak zavolají [DoModal](../atl/reference/cdialogimpl-class.md#domodal) metoda. Modální dialogové okno zavřít, volání [EndDialog](../atl/reference/cdialogimpl-class.md#enddialog) metoda z obslužné rutiny zpráv. Chcete-li vytvořit nemodální dialogové okno, volejte [vytvořit](../atl/reference/cdialogimpl-class.md#create) metoda místo `DoModal`. Pokud chcete odstranit nemodální dialogové okno, volání [destroywindow –](../atl/reference/cdialogimpl-class.md#destroywindow).  
  
 Zpracování událostí se automaticky provádí v [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md). Stejně jako obslužné rutiny v implementaci obslužné rutiny zpráv dialogových oken `CWindowImpl`-odvozené třídy. Pokud je zpráva konkrétní návratovou hodnotu, vrátí jej jako `LRESULT`. Vrácený `LRESULT` hodnoty jsou mapovat pomocí knihovny ATL pro správné zpracování dialogové okno správcem systému Windows. Podrobnosti najdete v tématu zdrojový kód pro [CDialogImplBaseT::DialogProc](../atl/reference/cdialogimpl-class.md#dialogproc) v atlwin.h.  
  
## <a name="example"></a>Příklad  
 Následující třídy implementuje dialogové okno:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/cpp/implementing-a-dialog-box_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

