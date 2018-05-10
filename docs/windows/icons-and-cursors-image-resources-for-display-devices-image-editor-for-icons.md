---
title: 'Ikony a kurzory: prostředky obrázků pro zařízení s displejem (Editor obrázků pro ikony) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a977629cbae140afa1463a7765f193a7519e1f68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>Ikony a kurzory: prostředky obrázků pro zařízení s displejem (editor obrázků pro ikony)
Ikony a kurzory jsou grafických prostředků, které mohou obsahovat více bitových kopií v různých velikostech a barevná schémata pro různé typy zobrazení zařízení. Kromě toho má kurzoru "aktivního bodu," umístění, které Windows používá ke sledování jeho umístění. Ikony a kurzory vytvářejí a upravit pomocí editoru bitové kopie, jako jsou rastrové obrázky a další bitové kopie.  
  
 Když vytvoříte nové ikony nebo kurzoru, editor obrázků nejprve vytvoří bitovou kopii standardní typu. Obrázek je původně vyplněn (transparentní) barvy obrazovky. Pokud je bitová kopie kurzoru, aktivní bod je původně levého horního rohu (souřadnice 0,0).  
  
 Editor obrázků ve výchozím nastavení podporuje vytváření další bitových kopií pro zařízení uvedené v následující tabulce. Bitové kopie pro jiná zařízení můžete vytvořit tak, že zadáte parametry šířky, výšky a počet barev do [dialogové okno vlastní obrázek](custom-image-dialog-box-image-editor-for-icons.md).  
  
> [!NOTE]
>  Pomocí editoru obrázků můžete prohlížet 32bitové obrázky, ale nemůžete je upravovat.  
  
|Barva|Šířka (v pixelech)|Výška (v pixelech)|  
|-----------|----------------------|-----------------------|  
|Černobílý tisk|16|16|  
|Černobílý tisk|32|32|  
|Černobílý tisk|48|48|  
|Černobílý tisk|64|64|  
|Černobílý tisk|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [Vytvoření nové obrázku zařízení (ikony nebo kurzoru)](../windows/creating-a-device-image-image-editor-for-icons.md)  
  
-   [Přidání obrázku pro zařízení s jiným zobrazením](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [Kopírování obrázku zařízení](../windows/copying-a-device-image-image-editor-for-icons.md)  
  
-   [Odstranění obrázku zařízení](../windows/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení](../windows/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [Vytvoření 256 barvami ikony nebo kurzoru](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [Nastavení aktivního bodu kurzoru](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)   
 [Ikony](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [Kurzory](http://msdn.microsoft.com/library/windows/desktop/ms646970)

