---
title: Určení umístění a velikost dialogového okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, size
- dialog boxes, positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4c6867f5ed3791414619257fec33db4c632553
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890574"
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

