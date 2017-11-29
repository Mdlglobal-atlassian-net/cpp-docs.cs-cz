---
title: "Úprava řetězce v prostředku informací o verzi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version
dev_langs: C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4547247a2ab9dc5b8ca98aae6838d9891f4ab49f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi
### <a name="to-edit-a-string-in-a-version-information-resource"></a>Chcete-li upravit řetězec v prostředku informací o verzi  
  
1.  Klikněte na položku jednou, potom znovu vyberte můžete začít s jeho úpravami. Provést změny přímo v tabulce informace o verzi nebo v [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Provedené změny se projeví na obou místech.  
  
     **Poznámka:** při úpravě **FILEFLAGS** klíče v editoru informací o verzi, můžete si všimnout nelze nastavit **ladění**, **privátní sestavení**, nebo  **Speciální sestavení** vlastnosti (v okně vlastností) pro soubory .rc:  
  
    -   Nastaví editor informací o verzi **ladění** vlastnost s #ifdef ve skriptu prostředků na základě **_DEBUG –** sestavení příznak.  
  
    -   Pokud **privátní sestavení** klíč má **hodnotu** nastavit v tabulce informace o verzi, odpovídající **privátní sestavení** vlastnost (v okně vlastností) **FILEFLAGS** klíč bude **True**. Pokud **hodnotu** je prázdné, bude vlastnost **False**. Podobně **speciální sestavení** klíč (v tabulce informace o verzi) je vázaný na **speciální sestavení** vlastnost **FILEFLAGS** klíč.  
  
 Informace o pořadí řetězce bloku můžete seřadit kliknutím na klíč nebo hodnota záhlaví sloupců. Tyto položky automaticky Změna uspořádání informace do vybrané pořadí.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor informací o verzi](../windows/version-information-editor.md)   
 [Informace o verzi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)
