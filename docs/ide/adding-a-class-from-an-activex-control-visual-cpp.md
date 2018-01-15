---
title: "Přidání třídy z ovládacího prvku ActiveX (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f059396c91ddb51247347d10e6c8f79a6c95522f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Přidání třídy z ovládacího prvku ActiveX (Visual C++)
Pomocí tohoto průvodce k vytvoření třídy knihovny MFC z rozhraní v ovládacím prvku ActiveX k dispozici. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../mfc/reference/creating-an-mfc-application.md), [MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládacího prvku ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z ovládacího prvku ActiveX automatizace.  
  
 Ovládací prvek ActiveX je opakovaně použitelné softwaru komponenta založená na modelu COM (Component Object), který podporuje širokou škálu funkcí technologie OLE a můžete přizpůsobit podle potřeb mnoho softwaru. ActiveX – ovládací prvky jsou navrženy pro použití v obyčejnou ActiveX – kontejnery ovládacích prvků i na Internetu v webové stránky.  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Přidání třídy knihovny MFC z ovládacího prvku ActiveX  
  
1.  Buď **Průzkumníku řešení** nebo [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název projektu, do které chcete přidat třídu ovládacího prvku ActiveX.  
  
2.  V místní nabídce klikněte na **přidat**a potom klikněte na **přidat třídu**.  
  
3.  V [přidat třídu](../ide/add-class-dialog-box.md) kliknutím na dialogové okno, v podokně šablon **třída knihovny MFC z ovládacího prvku ActiveX**a potom klikněte na **otevřete** zobrazíte [přidat třídu z ActiveX Řízení průvodce](../ide/add-class-from-activex-control-wizard.md).  
  
 V průvodci můžete přidat více než jedno rozhraní v ovládacím prvku ActiveX. Podobně můžete vytvořit třídy z více než jeden ovládací prvek ActiveX v rámci jedné relace průvodce.  
  
 Třídy můžete přidat z ovládacích prvků ActiveX registrovaných v systému, nebo můžete přidat třídu z ovládacích prvků ActiveX bez je první registraci v systému nachází v souborech knihovny typů (.tlb, .olb, DLL, .ocx nebo .exe). V tématu [registrace ovládacích prvků OLE](../mfc/reference/registering-ole-controls.md) Další informace o registraci ovládacích prvků ActiveX.  
  
 Průvodce vytvoří třídy knihovny MFC odvozené od [CWnd](../mfc/reference/cwnd-class.md) nebo z [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), u každého rozhraní přidáte z vybraný ovládací prvek ActiveX.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)