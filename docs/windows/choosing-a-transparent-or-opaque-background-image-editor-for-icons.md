---
title: "Výběr průhledného nebo neprůhledného pozadí (Editor obrázků pro ikony) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea4c5ae14bdf11583a3aba21dfd90e0a6f2fd92a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Výběr průhledného nebo neprůhledného pozadí (editor obrázků pro ikony)
Při přesunutí nebo kopírování výběru z bitové kopie, pixelů ve výběru, které odpovídají aktuálním barvu pozadí jsou ve výchozím nastavení transparentní; není jejich skrývat pixelů v cílovém umístění.  
  
 Můžete přejít z průhledné pozadí (výchozí) na neprůhledné pozadí a zpět. Při použití nástroje pro výběr, **průhledné pozadí** a **neprůhledné pozadí** zobrazí možnosti v modulu pro výběr možnost **Editor obrázků** panelu nástrojů (jak je vidět níže).  
  
 ![Možnosti pozadí & č. 45; průhledná nebo neprůhledná](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
Možnosti transparentní a neprůhledného na panelu nástrojů editoru obrázků  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Chcete-li přepnout mezi transparentní a neprůhledné pozadí  
  
1.  V **Editor obrázků** nástrojů, klikněte na tlačítko **možnost** selektor a potom klikněte na příslušnou pozadí:  
  
    -   **Neprůhledné pozadí (E)**: existující bitová kopie je po všech součástí výběr skryt.  
  
    -   **Průhledná pozadí (T)**: existující obrázek ukazuje prostřednictvím částí výběru, které odpovídají aktuálním barvu pozadí.  
  
 \-nebo –  
  
-   Na **Image** nabídky, zaškrtněte nebo zrušte **kreslení neprůhledných**.  
  
 Při výběru již je v platnosti změnit, jaké části obrázku jsou transparentní, můžete změnit barvu pozadí.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)