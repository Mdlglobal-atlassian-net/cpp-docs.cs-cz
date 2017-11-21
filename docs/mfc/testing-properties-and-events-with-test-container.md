---
title: "Testování vlastností a událostí pomocí testovacího kontejneru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88b1240666c15601f4a003d0d021fd12dc039fe1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="testing-properties-and-events-with-test-container"></a>Testování vlastností a událostí pomocí testovacího kontejneru
Aplikace – kontejner testů dodaný v jazyce Visual C++, je kontejneru ovládacího prvku ActiveX pro testování a ladění ovládacích prvků ActiveX. Kontejner testů umožňuje vývojáři řízení testování funkčnosti ovládacího prvku změnou jeho vlastnosti, vyvolání její metody a aktivuje její události. Kontejner testů můžete zobrazit protokoly oznámení datové vazby a také zajišťuje funkce pro testování trvalost funkce ovládacího prvku ActiveX: vlastnosti uložte do datového proudu nebo podúložiště, je znovu načíst a kontrolovat data uložená datového proudu. Tato část popisuje postup použití základní funkce – kontejner testů. Další informace, vyberte **pomoci** nabídky při spuštění – kontejner testů.  
  
### <a name="to-access-the-activex-control-test-container"></a>Pro přístup k kontejner testů ovládacích prvků ActiveX  
  
1.  Sestavení [TSTCON ukázka: kontejner testů ovládacích prvků ActiveX](../visual-cpp-samples.md).  
  
### <a name="to-test-your-activex-control"></a>K otestování ovládacího prvku ActiveX  
  
1.  Na **upravit** nabídky – kontejner testů, klikněte na tlačítko **vložit nový ovládací prvek**.  
  
2.  V **vložit ovládací prvek** pole, vyberte požadovaný ovládací prvek a klikněte na tlačítko **OK**. Ovládací prvek se zobrazí v kontejneru ovládacího prvku.  
  
    > [!NOTE]
    >  Pokud vlastní ovládací prvek není uvedený v **vložit ovládací prvek** dialogové okno zkontrolujte, zda je její zaregistrovaný **registrovat ovládací prvky** příkaz **souboru** nabídky testu Kontejner.  
  
 V tomto okamžiku můžete otestovat vlastnosti nebo události ovládacího prvku.  
  
#### <a name="to-test-properties"></a>K testování vlastnosti  
  
1.  Na **řízení** nabídky, klikněte na tlačítko **vyvolání metody**.  
  
2.  V **název metody** rozevíracího seznamu vyberte metodu propput – pro vlastnost, kterou chcete otestovat.  
  
3.  Upravit **hodnota parametru** nebo **typ parametru** a klikněte na **nastavit hodnotu** tlačítko.  
  
4.  Klikněte na tlačítko **Invoke** použít novou hodnotu do objektu.  
  
     Vlastnost nyní obsahuje novou hodnotu.  
  
#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Chcete-li otestovat události a zadat cílové umístění informací o události.  
  
1.  Na **možnosti** nabídky, klikněte na tlačítko **protokolování**.  
  
2.  Zadejte cíl informací o události.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Postupy: ladění ovládacího prvku ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

