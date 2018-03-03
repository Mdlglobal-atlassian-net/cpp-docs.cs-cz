---
title: "Změna velikosti jednotlivých ovládacích prvků | Microsoft Docs"
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
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b019cd2bbf68a4321bafd6dd960ffbcdba2dddf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sizing-individual-controls"></a>Změna velikosti jednotlivých ovládacích prvků
Úchyty použijte ke změně velikosti ovládacího prvku. Když ukazatel je umístěn na úchyt, změní tvar, který má znamenat pokynů, ve kterých jde změnit, ovládacího prvku. Aktivní úchyty jsou plné; Pokud je dutý úchyt, ovládacího prvku nelze změnit velikost podél této osy.  
  
 Můžete taky změnit velikost ovládacího prvku uchycení ovládacího prvku k vodítkům nebo okraje nebo přesunutím jeden přichyceno řízení a Průvodce mimo jiné.  
  
### <a name="to-size-a-control"></a>Chcete-li velikost ovládacího prvku  
  
1.  Vyberte ovládací prvek.  
  
2.  Přetáhněte úchyty ke změně velikosti ovládacího prvku:  
  
    -   Úchyty na začátku a konce změnit velikost vodorovně nebo svisle.  
  
    -   Úchyty v rozích změnit šířku a výšku.  
  
    > [!TIP]
    >  Řídicí jednotky jeden dialogu (DLU) můžete najednou změnit velikost tak, že podržíte stisknutou klávesu SHIFT a pomocí klávesy Šipka dolů a doprava.  
  
### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Chcete-li automaticky velikost ovládacího prvku podle textu v něm  
  
1.  Zvolte **velikost tak, aby obsah** z **formát** nabídky.  
  
 \-nebo –  
  
-   Klikněte pravým tlačítkem na ovládací prvek a vyberte **velikost tak, aby obsah** z místní nabídky.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

