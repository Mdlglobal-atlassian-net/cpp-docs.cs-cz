---
title: 'Kontejnery ovládacích prvků ActiveX: Použití ovládacích prvků v kontejneru než dialogovém okně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e190eb76702b1c6d246ac2aee9c22021955af7f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028100"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX – kontejnery ovládacích prvků: Použití ovládacích prvků v jiném kontejneru než dialogovém okně
V některých aplikací, jako jsou SDI nebo MDI aplikaci můžete k vložení ovládacího prvku v okně aplikace. **Vytvořit** členské funkce třídy obálky vložen Visual c++, můžete dynamicky vytvořit instanci ovládacího prvku bez nutnosti dialogového okna.  
  
 **Vytvořit** členské funkce má následující parametry:  
  
*lpszWindowName*<br/>
Ukazatel na text, který se zobrazí ve vlastnosti ovládacího prvku Text nebo Caption. (pokud existuje).  
  
*dwStyle*<br/>
Styly Windows. Úplný seznam najdete v tématu [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).  
  
*Rect*<br/>
Určuje velikost a umístění ovládacího prvku.  
  
*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku, obvykle `CDialog`. Nesmí se jednat o **NULL**.  
  
*nID*<br/>
Určuje ID ovládacího prvku a je možné odkazovat na ovládací prvek kontejnerem.  
  
 V zobrazení formuláře aplikace SDI by Příkladem použití této funkce dynamicky se vytvářejí ovládacího prvku ActiveX. Potom můžete vytvořit instanci ovládacího prvku `WM_CREATE` obslužné rutiny aplikace.  
  
 V tomto příkladu `CMyView` je třída hlavního zobrazení `CCirc` obálkovou třídu a msc H je záhlaví (. H) file obálkovou třídu.  
  
 Implementace této funkce je čtyři kroky.  
  
### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Dynamicky se vytvářejí ovládacího prvku ActiveX v okně – dialogové okno  
  
1.  Vložit msc H v CMYVIEW. H, těsně před `CMyView` definici třídy:  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  Přidání členské proměnné (typu `CCirc`) do části chráněné `CMyView` umístěné v CMYVIEW definici třídy. V:  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  Přidat `WM_CREATE` obslužné rutiny zpráv pro třídu `CMyView`.  
  
4.  Ve funkci obslužné rutiny `CMyView::OnCreate`, volání ovládacího prvku `Create` použití pracovat **to** ukazatele jako nadřazené okno:  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  Sestavte projekt znovu. Ovládací prvek KR vytvoří dynamicky při každém zobrazení vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

