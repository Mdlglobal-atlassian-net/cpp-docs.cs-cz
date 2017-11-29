---
title: "Změna vlastností vícenásobných kláves akcelerátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f85c83ad9ef582b918139863e0fdcca44817e800
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru
### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru  
  
1.  Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Vyberte klávesy akcelerátoru, kterou chcete změnit tak, že podržíte stisknutou **CTRL** klíče a klepněte na každé z nich.  
  
3.  Přejděte na [vlastnosti – okno](/visualstudio/ide/reference/properties-window) a zadejte hodnoty, které chcete všechny vybrané akcelerátorů do sdílené složky.  
  
    > [!NOTE]
    >  Každá hodnota modifikátor se zobrazí jako vlastnost typu Boolean v okně Vlastnosti. Pokud změníte [modifikátor](../windows/accelerator-modifier-property.md) hodnota v okně vlastností tabulky akcelerátorů zpracovává new – modifikátor jako doplněk k žádné modifikátory, které byly dříve existuje. Z toho důvodu Pokud nastavíte všechny hodnoty modifikátor musíte nastavit všechny, abyste zajistili, že každý akcelerátoru sdílí stejné nastavení modifikátor.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)