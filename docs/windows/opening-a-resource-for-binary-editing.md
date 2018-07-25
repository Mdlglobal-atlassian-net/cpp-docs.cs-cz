---
title: Otevření prostředku pro binární úpravy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c09cd825a5974422eaf757419f4ce890f5123100
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878483"
---
# <a name="opening-a-resource-for-binary-editing"></a>Otevření prostředku pro binární úpravy
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Chcete-li spustit Windows desktop prostředku pro binární úpravy  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), vyberte soubor konkrétní prostředek, který chcete upravit.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem na zdroj a klikněte na tlačítko **Open binární Data** z místní nabídky.  
  
    > [!NOTE]
    >  Pokud použijete [zobrazení prostředků](../windows/resource-view-window.md) okno otevřete prostředek ve formátu, Visual Studio nemůže rozpoznat (například RCDATA nebo vlastní prostředek), prostředku se automaticky otevře v editoru binární.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Chcete-li otevřít spravované prostředku pro binární úpravy  
  
1.  V Průzkumníku řešení vyberte soubor konkrétní prostředek, který chcete upravit.  
  
2.  Klikněte pravým tlačítkem prostředek a zvolte **otevřít v** z místní nabídky.  
  
3.  V **otevřít v** dialogovém okně vyberte **binární Editor**.  
  
    > [!NOTE]
    >  Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pracovat se soubory prostředků v spravované projekty. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
    > [!NOTE]
    >  Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Binární Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Binární Data pro dialogové okno zobrazí v binární Editor  
  
 V editoru binární (0x20 prostřednictvím 0x7E) jsou reprezentované jenom určité hodnoty ASCII. Znaky s diakritikou zobrazují jako tečky v části ASCII hodnota binární editor (v pravém panelu). "Tisknutelná" znaky jsou hodnoty ASCII 32 prostřednictvím 126.  
  
> [!NOTE]
>  Pokud chcete použít binární editor na prostředku již upravovaný v jiném okně editor, zavře okno editor jiných nejdřív.  
  
 **Požadavky**  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Binární editor](binary-editor.md)

