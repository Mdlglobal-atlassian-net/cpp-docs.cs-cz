---
title: Podokna (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a38341f6c6bcbcdec6bb4e6f5e5820fa759e6dab
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652021"
---
# <a name="window-panes-image-editor-for-icons"></a>Podokna (editor obrázků pro ikony)
**Editor obrázků** okno obvykle zobrazí obrázek do dvou podoken oddělené rozdělovač. Jedno zobrazení je skutečná velikost a druhý se zvětší (výchozí rozšíření faktor je 6). Zobrazení v těchto dvou podoken se automaticky aktualizují: změny, které provedete v jedno podokno se okamžitě zobrazí v jiném. Velikost podoken usnadňují práci na zvětšeným zobrazením bitové kopie, ve kterém můžete rozlišení jednotlivých pixelech a, ve stejnou dobu, můžete sledovat účinek práce na zobrazení skutečné velikosti obrázku.  
  
 V levém podokně používá tolik místa je potřeba (až polovinu **Image** okno) Chcete-li zobrazit zobrazení zvětšením 1:1 (výchozí) z image. Pravý panel zobrazuje přiblíženou bitové kopie (6:1 zvětšení ve výchozím nastavení). Můžete [změna měřítka zobrazení](../windows/changing-the-magnification-factor-image-editor-for-icons.md) v každé pomocí podokna **Magnify** nástroj [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo pomocí klávesové zkratky.  
  
 Můžete zvětšit menší podokně **Editor obrázků** okno a použijte dvě podokna pro zobrazení různých oblastech velký obrázek. Klikněte v podokně, vyberte ji.  
  
 Můžete změnit tak relativní velikosti podoken umístěním ukazatele na panelu rozdělení a přesunutí příčku směrem doprava nebo doleva. Pokud budete chtít pracovat na pouze jedno podokno, můžete příčku přesunout až po obou stranách.  
  
 Pokud **Editor obrázků** podokno se zvětšeným faktorem 4 nebo vyšší, můžete [zobrazit mřížku obrazových bodů](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md) , který odděluje citaci jednotlivých pixelech na obrázku.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)