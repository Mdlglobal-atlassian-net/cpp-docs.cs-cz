---
title: "Definování členských proměnných pro ovládací prvky dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog editor, defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f81b0d124db2a28b8d38c1a79d7569d8e46742b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defining-member-variables-for-dialog-controls"></a>Definování členských proměnných pro ovládací prvky dialogového okna
K definování proměnné člena pro libovolný ovládací prvek pole dialogové okno s výjimkou tlačítek, můžete použít následující metodu.  
  
> [!NOTE]
>  Tento článek se týká pouze ovládací prvky dialogového okna v projektu knihovny MFC. Projekty knihovny ATL měli používat **nové zprávy systému Windows a obslužné rutiny událostí** dialogové okno.  
  
### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>K definování proměnné člena pro ovládací prvek dialogového okna (bez tlačítko)  
  
1.  V [editoru dialogového okna](../windows/dialog-editor.md), vyberte ovládací prvek.  
  
2.  Při stiskněte **CTRL** klíče, klikněte dvakrát na dialogovém okně ovládacího prvku pole.  
  
     [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) se zobrazí.  
  
3.  Zadejte příslušné informace v **přidat proměnnou člen** průvodce. Další informace najdete v tématu [výměna dialogových dat](../mfc/dialog-data-exchange.md).  
  
4.  Klikněte na tlačítko **OK** se vraťte do editoru dialogových oken.  
  
    > [!TIP]
    >  Chcete-li přejít z libovolný ovládací prvek dialogové okno její existující obslužnou rutinu, dvakrát klikněte na ovládací prvek.  
  

  
 Můžete také **členské proměnné** kartě v **Průvodce třídou MFC** přidat nové proměnné členů pro zadanou třídu a zobrazit ty, které již byl definován.  
  
 Požadavky  
  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md)   
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Průvodce třídou MFC](../mfc/reference/mfc-class-wizard.md)   
 [Přidání třídy](../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)

