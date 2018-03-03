---
title: "Určení umístění a velikost dialogového okna | Microsoft Docs"
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
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03c4c6d6afb13a0e4ed8801838356ff0d1e851f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-location-and-size-of-a-dialog-box"></a>Určení umístění a velikosti dialogového okna
Umístění a velikost dialogového okna, stejně jako umístění a velikosti ovládacích prvků v něm, se měří v jednotky dialogu. Hodnoty jednotlivých ovládacích prvků a dialogové okno se zobrazí v pravém dolním rohu Visual Studio se na stavovém řádku po výběru.  
  
 Existují tři vlastnosti, které můžete nastavit v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) k určení, kde se zobrazí dialogové okno na obrazovce. Vlastnost Center je logická hodnota; Pokud nastavíte hodnotu na hodnotu True, dialogové okno vždy zobrazí v centru obrazovky. Pokud je nastavena na hodnotu False, pak můžete nastavit vlastnosti Pozice_x a Pozice_y explicitně definujte tam, kde na obrazovce, že zobrazí se dialogové okno. Pozice vlastnosti jsou posunutí hodnoty v levém horním rohu zobrazení oblast, která je definována jako {X = 0, Y = 0}. Pozice také podle **absolutní zarovnat** vlastnost: v případě hodnoty True souřadnice jsou relativní vzhledem k obrazovce, když má hodnotu False, souřadnice jsou relativní vzhledem k vlastník dialogovém okně.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

