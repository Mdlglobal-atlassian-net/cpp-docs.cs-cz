---
title: Editor obrázků pro ikony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors, graphics
- Image editor [C++]
- resource editors, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a4a80faf8718b1db103e15cba6ee97a73553490d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017741"
---
# <a name="image-editor-for-icons"></a>Editor obrázků pro ikony
Editor obrázků má rozsáhlou sadu nástrojů pro vytváření a úpravu obrázků a také funkce, které vám pomohou vytvořit rastry pro panel nástrojů. Kromě rastrových obrázků, ikon a kurzorů, můžete upravit obrázky ve formátu GIF nebo JPEG pomocí příkazů v **Image** nabídky a nástroje na **Editor obrázků** nástrojů.  
  
 Editou obrázků vám umožňuje:  
  
-   [Upravovat grafické prostředky](../windows/editing-graphical-resources-image-editor-for-icons.md)  
  
-   [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)  
  
-   [Práce s ikonami a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
  
-   [Používat klíče akcelerátoru pro příkazy v editoru obrázků](../windows/accelerator-keys-image-editor-for-icons.md)  
  
 **Editor obrázků** okno naleznete dvě zobrazení obrázku s rozdělovačem dvě podokna pro rozdělení. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru.  
  
 **Editor obrázků** okna můžete upravit podle vašich potřeb a preferencí. Je možné [změnit faktor zvětšení](../windows/changing-the-magnification-factor-image-editor-for-icons.md) a [zobrazit nebo skrýt mřížku obrazových bodů](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).  
  
> [!NOTE]
>  Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.  
  
## <a name="visual-studio-image-library"></a>Knihovna obrázků Visual Studio  
 Zdarma si můžete stáhnout **knihovna obrázků Visual Studio** obsahující mnoho animací, bitmap a ikon, které můžete použít ve svých aplikacích. Další informace o stažení knihovny naleznete v tématu [The knihovna obrázků Visual Studio](/visualstudio/designers/the-visual-studio-image-library).  
  
## <a name="managed-resources"></a>Spravované prostředky  
 Můžete použít **Image** editoru a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)   
 [Ikony](http://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)