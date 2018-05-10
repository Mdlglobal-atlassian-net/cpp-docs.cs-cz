---
title: Výběr průhledného nebo neprůhledného pozadí (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 244e6a63bc16b5e83bb8419dbe1b53741d566e56
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Výběr průhledného nebo neprůhledného pozadí (editor obrázků pro ikony)
Při přesunutí nebo kopírování výběru z bitové kopie, pixelů ve výběru, které odpovídají aktuálním barvu pozadí jsou ve výchozím nastavení transparentní; není jejich skrývat pixelů v cílovém umístění.  
  
 Můžete přejít z průhledné pozadí (výchozí) na neprůhledné pozadí a zpět. Při použití nástroje pro výběr, **průhledné pozadí** a **neprůhledné pozadí** zobrazí možnosti v modulu pro výběr možnost **Editor obrázků** panelu nástrojů (jak je vidět níže).  
  
 ![Možnosti na pozadí &#45; průhledná nebo neprůhledná](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
Možnosti transparentní a neprůhledného na panelu nástrojů editoru obrázků  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Chcete-li přepnout mezi transparentní a neprůhledné pozadí  
  
1.  V **Editor obrázků** nástrojů, klikněte na tlačítko **možnost** selektor a potom klikněte na příslušnou pozadí:  
  
    -   **Neprůhledné pozadí (E)**: existující bitová kopie je po všech součástí výběr skryt.  
  
    -   **Průhledná pozadí (T)**: existující obrázek ukazuje prostřednictvím částí výběru, které odpovídají aktuálním barvu pozadí.  
  
 \- nebo –  
  
-   Na **Image** nabídky, zaškrtněte nebo zrušte **kreslení neprůhledných**.  
  
 Při výběru již je v platnosti změnit, jaké části obrázku jsou transparentní, můžete změnit barvu pozadí.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)