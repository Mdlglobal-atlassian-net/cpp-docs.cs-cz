---
title: "Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 140be0aaaf614796d85fe30a33f93058cafafa57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné
Nejjednodušší způsob, jak přístup ovládacího prvku ActiveX v rámci jeho kontejnerové aplikace ovládacího prvku se má přidružit ovládacího prvku ActiveX k členské proměnné dialogu třídy, která bude obsahovat ovládacího prvku.  
  
> [!NOTE]
>  Toto není jedině pro přístup vloženému ovládacímu prvku z v rámci třídy kontejneru, ale pro účely tohoto článku je dostačující.  
  
### <a name="adding-a-member-variable-to-the-dialog-class"></a>Přidání členské proměnné pro třídu dialog  
  
1.  Ze třídy zobrazení klikněte pravým tlačítkem na hlavním dialogu třídy a místní nabídce. Například `CContainerDlg`.  
  
2.  V místní nabídce klikněte na **přidat** a potom **přidat proměnnou**.  
  
3.  V Průvodce přidáním členské proměnné, klikněte na **řídicí proměnná**.  
  
4.  V **ID ovládacího prvku** vyberte položku ID ovládacího prvku embedded ovládacího prvku ActiveX. Například `IDC_CIRCCTRL1`.  
  
5.  V **název proměnné** pole, zadejte název.  
  
     Například `m_circctl`.  
  
6.  Klikněte na tlačítko **Dokončit** potvrďte vybrané možnosti a ukončete Průvodce přidáním členské proměnné.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery ovládacích prvků ActiveX](../mfc/activex-control-containers.md)

