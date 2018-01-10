---
title: "Náhled prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- resource previews
- code, viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0eca56e607c916e28afc7bf513d853bcf6d94b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="previewing-resources"></a>Náhled prostředků
Zobrazení náhledu vaše prostředky můžete zobrazit grafické prostředků bez jejich otevření. Zobrazení náhledu je také užitečné pro spustitelné soubory, poté, co jste je kompilovat, protože identifikátory prostředků změnit na čísla. Vzhledem k tomu, že tyto číselné identifikátory často neposkytují dostatek informací, zobrazení náhledu prostředky vám pomůže rychle identifikovat.  
  
 Zobrazit náhled visual rozložení následující typy prostředků:  
  
-   Rastrový obrázek  
  
-   Dialogové okno  
  
-   Ikona  
  
-   Nabídka  
  
-   Kurzor  
  
-   Panel nástrojů  
  
 Funkce visual preview se nevztahuje na prostředky akcelerátoru, Manifest, řetězec tabulky a informace o verzi.  
  
### <a name="to-preview-resources"></a>Náhled prostředků  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md) nebo okna dokumentu, vyberte prostředek, například IDD_ABOUTBOX.  
  
     **Poznámka:** Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), klikněte **stránky vlastností** tlačítko.  
  
     \-nebo –  
  
3.  Na **zobrazení** nabídky, klikněte na tlačítko **stránky vlastností**.  
  
     Stránka vlastností pro prostředek otevře zobrazení Náhled prostředku. Potom můžete pomocí nahoru a dolů klávesy se šipkami přejděte ovládacího prvku strom zobrazení prostředků nebo okna dokumentu. Stránka vlastností zůstane otevřít a zobrazit jakémukoli prostředku, který má právě fokus a bude schopen zobrazit jejich náhled.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Postupy: otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Editory prostředků](../windows/resource-editors.md)

