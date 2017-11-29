---
title: "Postupy: Přidání podpory MFC do souborů skriptu prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.resvw.add.MFC
dev_langs: C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d931c1309d583b8904afa403130411e495e0408
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Postupy: Přidání podpory MFC do souborů skriptu prostředků
Za normálních okolností při vytváření aplikace knihovny MFC pro Windows pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), Průvodce generuje základní sadu soubory (včetně souboru skriptu (.rc) prostředků), který obsahuje hlavní funkce Microsoft Foundation třídy (MFC). Ale pokud upravujete soubor .rc pro aplikace Windows, která není založena na MFC, následující funkce, které jsou specifické pro rozhraní MFC framework nejsou k dispozici:  
  
-   Průvodci kódem MFC (označovaly jako "[MFC ClassWizard](http://msdn.microsoft.com/en-us/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)")  
  
-   Výzva řetězce nabídky  
  
-   Zobrazovat obsah pro ovládací prvky pole se seznamem  
  
-   Hostování ovládacího prvku ActiveX  
  
 Podpora MFC ale můžete přidat existující soubory .rc, které nemají ho.  
  
### <a name="to-add-mfc-support-to-rc-files"></a>Přidání podpory MFC do soubory .rc  
  
1.  Otevření souboru skriptu prostředků.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [zobrazení prostředků](../windows/resource-view-window.md), zvýrazněte složce prostředky (například MFC.rc).  
  
3.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), nastavte **MFC režimu** vlastnost **True**.  
  
    > [!NOTE]
    >  Kromě nastavení tento příznak, musí být soubor .rc součástí projektu knihovny MFC. Například pouze nastavení **MFC režimu** k **True** na soubor .rc ve Win32 projektu nebude získáte žádnou z funkcí MFC.  
  

  
 **Požadavky**  
  
 MFC  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)