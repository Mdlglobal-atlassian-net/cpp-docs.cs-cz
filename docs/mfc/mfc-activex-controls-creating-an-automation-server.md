---
title: "Ovládací prvky MFC ActiveX: Vytvoření serveru automatizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56b05c85212630b8e368817006098aeff2ceb832
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC – ovládací prvky ActiveX: Vytvoření serveru automatizace
Můžete vyvíjet ovládacího prvku ActiveX knihovny MFC jako serveru automatizace pro účely programově vložení tohoto ovládacího prvku v jiné aplikaci a volání metod v ovládacím prvku z aplikace. Takový ovládací prvek bude stále k dispozici pro hostování v kontejneru ovládacího prvku ActiveX.  
  
### <a name="to-create-a-control-as-an-automation-server"></a>Vytvoření ovládacího prvku jako serveru automatizace  
  
1.  [Vytvoření](../mfc/reference/mfc-activex-control-wizard.md) ovládacího prvku.  
  
2.  [Přidejte metody](../mfc/mfc-activex-controls-methods.md).  
  
3.  Přepsání [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed). Další informace najdete v článku znalostní báze Knowledge Base Q146120.  
  
4.  Vytvoření ovládacího prvku.  
  
### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Pro přístup programu ke metody v serveru automatizace  
  
1.  Vytvořit aplikaci, například, [MFC exe](../mfc/reference/mfc-application-wizard.md).  
  
2.  Na začátku `InitInstance` fungovat, přidejte následující řádek:  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  V zobrazení tříd, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat třídu z typelib** Import knihovny typů.  
  
     Soubory s .h přípony názvu souboru a sada se přidá do projektu.  
  
4.  V záhlaví souboru třídy, kde bude volat jednu nebo více metod v ovládacím prvku ActiveX, přidejte následující řádek: `#include filename.h`, kde název souboru je název souboru záhlaví, která byla vytvořena, když jste naimportovali knihovny typů.  
  
5.  Ve funkci, kde budou provedeny volání metody v ovládacím prvku ActiveX přidejte kód, který vytvoří objekt třídu obálky ovládacího prvku a vytvořit objekt ActiveX. Například následující kód MFC vytvoří `CCirc` ovládací prvek, získá vlastnost popisek a při kliknutí na tlačítko OK v dialogovém okně se zobrazí výsledek:  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 Pokud přidáte metody do ovládacího prvku ActiveX po použití v aplikaci, můžete začít používat nejnovější verzi ovládacího prvku v aplikaci tak, že odstraníte soubory, které byly vytvořeny při importu knihovny typů. Znovu proveďte importujte knihovny typů.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)

