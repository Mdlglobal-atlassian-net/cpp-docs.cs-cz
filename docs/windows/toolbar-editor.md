---
title: Editor panelu nástrojů (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c51c8a5dc321d61b6167fb6a1e5b71d52145d81d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316949"
---
# <a name="toolbar-editor-c"></a>Editor panelu nástrojů (C++)

**Nástrojů** editor umožňuje vytvářet prostředky nástrojů jazyka C++ a rastrové obrázky převést prostředky panelu nástrojů. **Nástrojů** editor používá grafické zobrazení zobrazíte panel nástrojů a tlačítka, která se velmi podobají, jak bude vypadat dokončené aplikace.

S **nástrojů** editoru, můžete:

- [Vytváření nových panelů nástrojů a tlačítka](../windows/creating-new-toolbars.md)

- [Převádění bitmap na prostředky panelu nástrojů](../windows/converting-bitmaps-to-toolbars.md)

- [Vytváření, přesunutí a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [Vytváření popisů tlačítek](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

**Nástrojů** okno editoru naleznete dvě zobrazení obrázku tlačítka, stejně jako okno editoru obrázků. Rozdělit pruh odděluje. Můžete přetáhnout příčku ze strany na stranu, a změnit tak relativní velikosti podoken. Aktivní podokno zobrazuje hranici výběru. Nad dvě zobrazení obrázku je panel nástrojů předmět.

![Editor panelu nástrojů](../mfc/media/vctoolbareditor.gif "vcToolbarEditor")  
Editor panelu nástrojů

**Nástrojů** editoru je podobný **Image** editor ve funkcích. Položky nabídky, grafické nástroje a rastrový obrázek mřížky jsou stejná jako v **Image** editoru. Příkaz nabídky **Image** nabídky, aby bylo možné přepínat mezi **nástrojů** editoru a **Image** editoru. Další informace o používání **grafiky** nástrojů **barvy** palety, nebo **Image** nabídky, naleznete v tématu [Editor obrázků](../windows/image-editor-for-icons.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)  
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)