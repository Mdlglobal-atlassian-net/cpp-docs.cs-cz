---
title: Změna velikosti celého obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], resizing images
- size [C++], images
- images [C++], resizing
- resizing images
ms.assetid: 10782937-7eb4-4340-bdec-618ee7d7904b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2326918b6efd4c8da5f74527166d8f373dbacefc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376835"
---
# <a name="resizing-an-entire-image-image-editor-for-icons"></a>Změna velikosti celého obrázku (editor obrázků pro ikony)

### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Změna velikosti celého obrázku pomocí okna Vlastnosti

1. Otevřete obrázek, jehož vlastnosti chcete změnit.

2. V **šířka** a **výška** polích v [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte dimenze, které chcete.

   Pokud hodláte zvýšit velikost bitové kopie, **Image** editor rozšiřuje na obrázku vpravo směrem dolů, nebo obojí a vyplní nové oblasti aktuální barvou pozadí. Obrázek není roztažená.

   Pokud jsou zmenšit velikost bitové kopie, **Image** editor obrázek ořízne tak, na pravé nebo dolní okraj nebo obojí.

   > [!NOTE]
   > Můžete použít **šířka** a **výška** vlastnosti, které chcete změnit velikost pouze celého obrázku, ne pro změnu velikosti částečného výběru.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Změna velikosti obrázku](../windows/resizing-an-image-image-editor-for-icons.md)