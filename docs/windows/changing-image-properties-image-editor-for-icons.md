---
title: "Změna vlastností obrázku (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96122b2bdc6419b41cd0e00cb544955d8d7c8463
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Změna vlastností obrázku (editor obrázků pro ikony)
Můžete nastavit nebo upravit vlastnosti použití bitové kopie [vlastnosti – okno](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-change-an-images-properties"></a>Chcete-li změnit vlastnosti bitové kopie  
  
1.  Otevřete obrázek **Image** editor.  
  
2.  V **vlastnosti** okně změnit některé nebo všechny vlastnosti pro image.  
  
    |Vlastnost|Popis|  
    |--------------|-----------------|  
    |**Barvy**|Určuje barevné schéma pro bitovou kopii. Vyberte barvu černobílý tisk, 16, nebo 256 nebo hodnotu True. Pokud již máte vykreslovat bitové kopie s 16 barev palety, když vyberete černobílý tisk, budou náhrady černobílý pro barvy v bitové kopii. Vždy kontrast nezachová: například přiléhající oblasti red a zelená obě převedou do černé.|  
    |**Název souboru**|Určuje název souboru bitové kopie. Ve výchozím nastavení Visual Studio přiřadí základní filename vytvořené odebrání první čtyři znaky ("IDB_") z výchozí identifikátor prostředku (IDB_BITMAP1) a přidání příslušná rozšíření. Název souboru bitové kopie v tomto příkladu bude BITMAP1.bmp. Můžete ho přejmenovat MYBITMAP1.bmp.|  
    |**Výška**|Nastaví výšku obrázku (v pixelech). Výchozí hodnota je 48. Je oříznutý obrázek nebo prázdné místo je přidán pod existující bitová kopie.|  
    |**ID**|Nastaví identifikátor prostředku. Pro bitovou kopii, Microsoft Visual Studio, ve výchozím nastavení, přiřadí identifikátor další k dispozici v řadě: IDB_BITMAP1, IDB_BITMAP2, a tak dále. Podobně jako názvy jsou použity pro ikony a kurzory.|  
    |**Palety**|Změny barev vlastnosti. Klikněte dvakrát na výběr barvy a zobrazení [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Zadejte barvu zadáním hodnoty RGB nebo HSL do příslušné textových polí.|  
    |**SaveCompressed**|Určuje, zda obrázek v komprimovaném formátu. Tato vlastnost je pouze pro čtení. Visual Studio neumožňuje pro uložení bitové kopie v komprimovaném formátu, takže pro všechny bitové kopie vytvořené v sadě Visual Studio, bude mít tato vlastnost **False**. Pokud v sadě Visual Studio otevřete zkomprimovaná bitová kopie (vytvořený v jiné aplikaci), bude mít tato vlastnost **True**. Pokud jste uložili komprimované bitové kopie pomocí sady Visual Studio, nekomprimované a tato vlastnost se vrátí zpět na **False**.|  
    |**Šířka**|Nastaví šířku obrázku (v pixelech). Výchozí hodnota pro Bitmap je 48. Je oříznutý obrázek nebo prázdného místa se přidá napravo od existující bitová kopie.|  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

