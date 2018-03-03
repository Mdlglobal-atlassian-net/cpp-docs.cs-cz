---
title: "Kontejnery ovládacích prvků ActiveX: Použití ovládacích prvků v kontejneru než dialogovém okně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c380d0a525c2f026054ebae1812450c4d4634c1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX – kontejnery ovládacích prvků: Použití ovládacích prvků v jiném kontejneru než dialogovém okně
V některých aplikace, jako je například SDI a MDI aplikace můžete pro vložení ovládacího prvku v okně aplikace. **Vytvořit** funkce člena třídy obálky vložit pomocí Visual C++, můžete dynamicky, vytvořte instanci ovládacího prvku bez nutnosti dialogové okno.  
  
 **Vytvořit** – členská funkce má následující parametry:  
  
 `lpszWindowName`  
 Ukazatel na text, který se zobrazí v textu nebo popisek ovládacího prvku (pokud existuje).  
  
 `dwStyle`  
 Styly systému Windows. Úplný seznam najdete v tématu [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku.  
  
 `pParentWnd`  
 Určuje ovládacího prvku nadřazeného okna, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku a umožňuje kontejnerem odkazovat na ovládací prvek.  
  
 Příkladem použití této funkce vytvořit dynamicky ovládacího prvku ActiveX by v zobrazení formuláře aplikace SDI. Potom můžete vytvořit instanci ovládacího prvku `WM_CREATE` obslužná rutina aplikace.  
  
 V tomto příkladu `CMyView` je třída hlavního zobrazení `CCirc` je obálková třída a msc H je záhlaví (. H) soubor obálkovou třídu.  
  
 Implementace této funkce je čtyři kroky.  
  
### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>V okně – dialogové okno vytvořit dynamicky ovládacího prvku ActiveX  
  
1.  Vložit msc H v CMYVIEW. H, těsně před `CMyView` definici třídy:  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  Přidání členské proměnné (typu `CCirc`) do části chráněné `CMyView` umístěný v CMYVIEW definici třídy. V:  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  Přidat `WM_CREATE` popisovač zpráv pro třídu `CMyView`.  
  
4.  Ve funkci obslužná rutina `CMyView::OnCreate`, volání ovládacího prvku `Create` funkce pomocí **to** ukazatel jako nadřazené okno:  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  Znovu sestavte projekt. Str ovládacího prvku se dynamicky vytvoří vždy, když je vytvořeno zobrazení aplikace.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

