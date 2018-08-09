---
title: Změna vlastností obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a5ffd1f9478b43de487e37fdd80a5b709152296
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648568"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Změna vlastností obrázku (editor obrázků pro ikony)
Můžete nastavit nebo upravit vlastnosti image pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-change-an-images-properties"></a>Chcete-li změnit vlastnosti obrázku  
  
1.  Otevřít obrázek v **Image** editoru.  
  
2.  V **vlastnosti** okně změnit některé nebo všechny vlastnosti pro vaši image.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |**Barvy**|Určuje barevné schéma pro bitovou kopii. Vyberte **monochromatický**, **16**, nebo **256**, nebo **True Color**. Pokud byl nakreslen již obrázek s barevnou paletu na 16 barev, výběru **monochromatický** způsobí, že nahrazení černá a bílá pro barvy v bitové kopii. Není vždy udržují kontrast: například sousední oblasti červenou a zelenou obě převedou na černou.|  
    |**Název souboru**|Určuje název souboru obrázku. Ve výchozím nastavení přiřadí sady Visual Studio z výchozího identifikátoru prostředku (IDB_BITMAP1) a přidání příslušné rozšíření základní název souboru vytvořené tak, že odeberete první čtyři znaky ("IDB_"). Název souboru bitové kopie v tomto příkladu by měl být `BITMAP1.bmp`. Můžete ho přejmenovat `MYBITMAP1.bmp`.|  
    |**Výška**|Nastaví výšku obrázku (v pixelech). Výchozí hodnota je 48. Oříznutí obrázku nebo je prázdné místo přidání následujících stávající bitovou kopii.|  
    |**ID**|Nastaví identifikátor prostředku. Pro bitovou kopii, Microsoft Visual Studio ve výchozím nastavení, přiřadí identifikátor další dostupné v řadě: IDB_BITMAP1, IDB_BITMAP2, a tak dále. Podobně jako názvy jsou použity pro ikony a kurzory.|  
    |**Paleta**|Změny barev vlastnosti. Dvakrát klikněte na Zobrazit a vybrat barvu [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definujte barvu tak, že zadáte hodnoty vyjadřující příslušná textová pole.|  
    |**SaveCompressed**|Označuje, zda je na obrázku ve formátu komprimované. Tato vlastnost je pouze pro čtení. Visual Studio neumožňuje uložit obrázky v komprimovaném formátu, tak pro všechny obrázky vytvořené v sadě Visual Studio, bude mít tato vlastnost **False**. Pokud v sadě Visual Studio otevřete komprimovanou bitovou kopii (vytvořený v jiném programu), bude mít tato vlastnost **True**. Pokud jste uložili komprimované bitové kopie pomocí sady Visual Studio, nekomprimovaný a tato vlastnost se vrátí zpět k **False**.|  
    |**Šířka**|Nastaví šířku obrázku (v pixelech). Výchozí hodnota pro rastrových obrázků je 48. Oříznutý obrázek nebo napravo od existující bitová kopie se přidá mezeru.|  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)