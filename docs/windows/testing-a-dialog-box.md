---
title: "Testování dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes, testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca6e6cd8dd9f7d67ba8a000f33143a12c0978a25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="testing-a-dialog-box"></a>Testování dialogového okna
Při návrhu dialogové okno, můžete simulaci a kontrolu její chování bez kompilace vašeho programu. V tomto režimu můžete:  
  
-   Zadejte text, vyberte pole se seznamem seznamech, zapnout nebo vypnout možnosti a zvolte příkazy.  
  
-   Testování pořadí.  
  
-   Otestujte seskupení ovládacích prvků, jako je například přepínací tlačítka a zaškrtávací políčka.  
  
-   Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.  
  
    > [!NOTE]
    >  Připojení k poli Kód dialogu provedené pomocí průvodců nejsou součástí simulace.  
  
 Při testování dialogového okna, obvykle se zobrazí v umístění, která je relativní k hlavní okno programu. Pokud nastavíte dialogových oken absolutní zarovnat vlastnost na hodnotu True, zobrazí se dialogové okno na pozici, která je relativní k levého horního rohu obrazovky.  
  
### <a name="to-test-a-dialog-box"></a>K testování dialogového okna  
  
1.  Editor dialogových oken při aktivní okno na řádku nabídek zvolte **formátu**, **Test – dialogové okno**.  
  
2.  Na konec simulace, stiskněte klávesy Esc nebo zvolte pouze **Zavřít** tlačítka v dialogovém okně testování.  
  
 Informace o tom, jak přidat prostředky do spravovaných projekty najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Editor dialogových oken](../windows/dialog-editor.md)   
 [Zobrazení nebo skrytí panelu nástrojů editoru dialogového okna](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

