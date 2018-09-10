---
title: Výběr průhledného nebo neprůhledného pozadí (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c0c4c306191af519103c65b39e3bb89afdb47f9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313478"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>Výběr průhledného nebo neprůhledného pozadí (editor obrázků pro ikony)

Když přesouváte nebo kopírujete z bitové kopie s výběrem, žádné pixelech ve výběru, které odpovídají barvě pozadí jsou ve výchozím nastavení transparentní; Ne, zakrýt pixelů v cílovém umístění.

Můžete přepnout z průhledné pozadí (výchozí) do neprůhledné pozadí a zpět. Při použití nástroje pro výběr, **průhledné pozadí** a **neprůhledné pozadí** možnosti se zobrazí **možnost** selektor na **Editor obrázků** nástrojů (jak je vidět níže).

![Možnosti pozadí &#45; neprůhledné nebo průhledné](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
**Možnosti transparentní a neprůhledné** na **panelu nástrojů editoru obrázků**

### <a name="to-switch-between-a-transparent-and-opaque-background"></a>Chcete-li přepnout mezi transparentní a neprůhledné pozadí

1. V **Editor obrázků** nástrojů, klikněte na tlačítko **možnost** selektor a potom klikněte na tlačítko na pozadí odpovídající:

   - `Opaque Background (O)`: Existující image je po všech součástí výběr skryt.

   - `Transparent Background (T)`: Existujícího obrázku prostřednictvím částí výběru, které odpovídají barvě pozadí.

\- nebo –

- Na **Image** nabídky, zaškrtněte nebo zrušte **kreslení neprůhledných**.

Při výběru je již platná, chcete-li změnit, které části obrázku je transparentní, můžete změnit barvu pozadí.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)