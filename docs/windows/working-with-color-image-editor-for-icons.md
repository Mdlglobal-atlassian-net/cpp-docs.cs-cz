---
title: Práce s barvou (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors, Image editor
- colors [C++]
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f9016e36ce6b081446a00136445fd7ebdd5a341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891656"
---
# <a name="working-with-color-image-editor-for-icons"></a>Práce s barvou (editor obrázků pro ikony)
Editor obrázků obsahuje řadu funkcí, které konkrétně zpracování a přizpůsobení barev. Můžete nastavit barvu popředí nebo pozadí, vyplnění ohraničené oblasti barvou nebo vybrat barvu v obrázku chcete použít jako aktuální barvu popředí nebo pozadí. Můžete použít nástroje na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) společně s barevná paleta v [barvy – okno](../windows/colors-window-image-editor-for-icons.md) k vytvoření bitové kopie.  
  
 Všechny barvy pro černobílý tisk a 16 barev obrázků se zobrazí v okně barvy palety barev. Kromě 16 standardní barvy můžete vytvořit své vlastní barvy. Změna barvy palety hned změnit barvu odpovídající v bitové kopii.  
  
 Při práci s 256 barvami ikonu a kurzor Image, vlastnost barvy v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) se používá. Další informace najdete v tématu [vytváření 256 barvami ikony nebo kurzoru s](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md).  
  
> [!NOTE]
>  Pomocí editoru obrázků můžete prohlížet 32bitové obrázky, ale nemůžete je upravovat.  
  
 Můžete také vytvořit Image barvami hodnotu true. Však true barva ukázky se nezobrazí v úplné palety v okně barvy; Zobrazí se pouze v oblasti indikátor barvy popředí nebo na pozadí. Hodnota TRUE, barvy jsou vytvořené pomocí [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 Můžete uložit přizpůsobené barev palety na disku a podle potřeby je znovu načíst. Paletu barev, kterou jste naposledy použili je uložen v registru a automaticky načte při dalším spuštění sady Visual Studio.  
  
-   [Výběr barev popředí nebo pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [Vyplnění ohraničené oblasti obrázku barvou](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [Výběr barvy z obrázku, která se použije jinde](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [Výběr průhledného nebo neprůhledného pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [Převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [Přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [Ukládání a načítání různých barevných palet](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [Barvy – okno](../windows/colors-window-image-editor-for-icons.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   

