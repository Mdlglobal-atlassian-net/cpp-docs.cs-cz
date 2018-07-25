---
title: Zobrazení a úprava prostředků v editoru prostředků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resourceview
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1afa1377b222789243706cf3c5e61f45b4fcd1a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891815"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Zobrazení a úprava prostředků v editoru prostředků
Každý typ prostředku má editoru prostředků specifické pro daný typ prostředku. Můžete Změna uspořádání, změnit velikost, přidávání ovládacích prvků a funkce nebo v opačném případě upravte aspektů prostředek přidružené editoru. Můžete také upravit prostředek v [textovém formátu](../windows/how-to-open-a-resource-script-file-in-text-format.md) a [binární formát](../windows/opening-a-resource-for-binary-editing.md).  
  
 Některé typy prostředků jsou jednotlivé soubory, které můžete importovat a použít různé způsoby; mezi ně patří, rastrové obrázky, ikony, kurzory, panely nástrojů a soubory html. Tyto prostředky mají názvy souborů a také [identifikátory prostředků](../windows/symbols-resource-identifiers.md). Ostatní, například dialogových oken, nabídek a tabulek řetězců v projektech, Win32, existuje jenom jako součást souboru skriptu (.rc) prostředků nebo prostředek souboru šablony (.rct).  
  
> [!NOTE]
>  Vlastnosti prostředku [lze upravit pomocí vlastností okna](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Prostředky Win32  
 Můžete přístup k prostředkům Win32 ve [zobrazení prostředků](../windows/resource-view-window.md) podokně.  
  
#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Chcete-li zobrazit Win32 prostředků v editoru prostředků  
  
1.  Vyberte **zobrazení prostředků** z **zobrazení** nabídky.  
  
2.  Pokud není okno zobrazení zdrojů okno nejvyšší, klikněte na tlačítko **zobrazení prostředků** kartě a převeďte ho na začátek.  
  
3.  Ze zobrazení zdrojů rozbalte složku pro projekt, který obsahuje prostředky, které chcete zobrazit. Pokud chcete zobrazit dialogové okno prostředek, například rozbalte složku dialogové okno.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Dvakrát klikněte na prostředek, například IDD_ABOUTBOX.  
  
     Prostředek se otevře ve vhodném editoru. Pro dialogové okno prostředky, například prostředek otevře v editoru dialogových oken.  
  
     Můžete také [zobrazit prostředky v souboru .rc (prostředků skript) bez nutnosti otevřít projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
#### <a name="to-delete-an-existing-win-32-resource"></a>Chcete-li odstranit existující prostředek Win 32  
  
1.  V zobrazení zdrojů rozbalte uzel pro typ prostředku.  
  
2.  Klikněte pravým tlačítkem na prostředků, kterou chcete odstranit a zvolit **odstranit** z místní nabídky.  
  
    > [!NOTE]
    >  Můžete odstranit prostředek pomocí příkazu stejnou místní nabídky, když máte soubor otevřete v okně dokumentu mimo projekt.  
  
## <a name="resources-in-managed-projects"></a>Prostředky ve spravované projekty  
 Protože spravované projekty nepoužívají soubory skriptu prostředků, musíte otevřít vaše prostředky z **Průzkumníku řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pracovat se soubory prostředků v spravované projekty. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
#### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Chcete-li zobrazit spravovaných prostředků v editoru prostředků  
  
1.  V Průzkumníku řešení klikněte dvakrát na prostředek, například Bitmap1.bmp.  
  
     Prostředek se otevře ve vhodném editoru.  
  
#### <a name="to-delete-an-existing-managed-resource"></a>Chcete-li odstranit existující spravovaný prostředek  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na prostředků, kterou chcete odstranit a zvolit **odstranit** z místní nabídky.  
  
### <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)

