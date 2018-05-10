---
title: Obrázek nabídky (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- Image menu
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bfeeda8d358bf3144cd5c3168686561b3586581
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="image-menu-image-editor-for-icons"></a>Nabídka obrázku (editor obrázků pro ikony)
Nabídka obrázku, která se zobrazí jenom v případě, že je aktivní editor obrázků, obsahuje příkazy pro úpravy bitové kopie, Správa palety barev a nastavení možností okno Editor obrázků. Příkazy pro použití obrázky zařízení kromě toho jsou k dispozici při práci s ikony a kurzory.  
  
 **Invertování barev**  
 Invertuje výběr barev. Další informace najdete v tématu [převrácení barev ve výběru](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).  
  
 **Překlopit vodorovných**  
 Převrátí bitovou kopii nebo výběr vodorovně. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Překlopit Vertical**  
 Převrátí bitovou kopii nebo výběr svisle. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Otočit 90 stupňů.**  
 Otočí obrázek nebo výběr 90 stupňů. Další informace najdete v tématu [překlopení obrázku](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Zobrazit barvy – okno**  
 Otevře se [barvy – okno](../windows/colors-window-image-editor-for-icons.md), v němž můžete vybrat barvy použité pro bitové kopie. Další informace najdete v tématu [práce s barvou](../windows/working-with-color-image-editor-for-icons.md).  
  
 **Použijte výběr jako štětce**  
 Umožňuje vytvoření vlastního štětce z část obrázku. Výběr stane vlastního štětce, která distribuuje barev ve výběru v bitovou kopii. Zkopíruje výběr jsou ponechána v přetahování cestě. Tím pomaleji přetažení, jsou provedeny další kopie. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 **Kopírování a výběr obrysu**  
 Vytvoří kopii aktuální výběr a popisuje ho. Pokud barvu pozadí je obsažena v aktuálním výběru, bude vyloučena Pokud máte [transparentní](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) vybrané.  
  
 **Upravit barvy**  
 Otevře se [výběr barvy vlastní](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), která umožňuje přizpůsobit barvy, můžete použít pro bitové kopie. Další informace najdete v tématu [přizpůsobení nebo změna barev](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 **Zatížení palety**  
 Otevře se [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), což umožňuje načíst barvy palety dříve uloží do souboru PAL.  
  
 **Uložit palety**  
 Barvy palety uloží do souboru PAL.  
  
 **Kreslení neprůhledné**  
 Když vyberete, bude aktuální výběr neprůhledná. Pokud zaškrtnutí políčka zrušeno, díky aktuální výběr transparentní. Další informace najdete v tématu [výběr neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 **Editor panelu nástrojů**  
 Otevře se [dialogové okno Nový prostředek panelu nástrojů](../windows/new-toolbar-resource-dialog-box.md).  
  
 **Nastavení mřížky**  
 Otevře se [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md) ve kterém můžete zadat mřížky pro bitové kopie.  
  
 **Nový obrázek – typ**  
 Otevře se [nový \<zařízení > dialogové okno typ obrázku](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Jeden ikonu prostředků může obsahovat několik imagí různě; Windows můžete použít velikost příslušnou položku v závislosti na tom, jak se bude, který se má zobrazit. Nedojde ke změně velikosti na ikonu nový typ zařízení, ale spíš vytvoří novou bitovou kopii v rámci ikonu. Pouze u ikony a kurzory.  
  
 **Aktuální typ obrázku ikony nebo kurzoru**  
 Otevře podnabídky, které uvádí první dostupné kurzoru nebo ikonu Image (první devět). Poslední příkaz v podnabídce **více...** , otevře se [otevřete \<zařízení > dialogové okno Obrázek](../windows/open-device-image-dialog-box-image-editor-for-icons.md).  
  
 **Odstranit typ obrázku**  
 Odstraní vybrané zařízení image.  
  
 **Nástroje**  
 Spustí dílčí, který obsahuje všechny nástroje, které jsou k dispozici prostřednictvím [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

