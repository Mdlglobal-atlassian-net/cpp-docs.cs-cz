---
title: Úprava řetězce v prostředku informací o verzi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80795f912ab41809b19e77bd33f56243541d4de1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="editing-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi
### <a name="to-edit-a-string-in-a-version-information-resource"></a>Chcete-li upravit řetězec v prostředku informací o verzi  
  
1.  Klikněte na položku jednou, potom znovu vyberte můžete začít s jeho úpravami. Provést změny přímo v tabulce informace o verzi nebo v [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Provedené změny se projeví na obou místech.  
  
     **Poznámka:** při úpravě **FILEFLAGS** klíče v editoru informací o verzi, můžete si všimnout nelze nastavit **ladění**, **privátní sestavení**, nebo **Speciální sestavení** vlastnosti (v okně vlastností) pro soubory .rc:  
  
    -   Nastaví editor informací o verzi **ladění** vlastnost s #ifdef ve skriptu prostředků na základě **_DEBUG –** sestavení příznak.  
  
    -   Pokud **privátní sestavení** klíč má **hodnotu** nastavit v tabulce informace o verzi, odpovídající **privátní sestavení** vlastnost (v okně vlastností) **FILEFLAGS** klíč bude **True**. Pokud **hodnotu** je prázdné, bude vlastnost **False**. Podobně **speciální sestavení** klíč (v tabulce informace o verzi) je vázaný na **speciální sestavení** vlastnost **FILEFLAGS** klíč.  
  
 Informace o pořadí řetězce bloku můžete seřadit kliknutím na klíč nebo hodnota záhlaví sloupců. Tyto položky automaticky Změna uspořádání informace do vybrané pořadí.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor informací o verzi](../windows/version-information-editor.md)   
 [Informace o verzi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

