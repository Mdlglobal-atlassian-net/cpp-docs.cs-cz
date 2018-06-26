---
title: 'Kontejnery ovládacích prvků ActiveX: Připojení ovládacího prvku ActiveX k členské proměnné | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3aa243ab8c0fb49e20e5b7485acdcd8bb808831
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930465"
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
  
     Například *m_circctl*.  
  
6.  Klikněte na tlačítko **Dokončit** potvrďte vybrané možnosti a ukončete Průvodce přidáním členské proměnné.  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

