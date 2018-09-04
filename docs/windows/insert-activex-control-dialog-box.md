---
title: Vložit ovládací prvek ActiveX – dialogové okno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef8f2142f00b862ff198df9c75e142dc66a049b5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689961"
---
# <a name="insert-activex-control-dialog-box"></a>Dialogové okno Vložit ovládací prvek ActiveX

Toto dialogové okno umožňuje [vložení ovládacích prvků ActiveX do vašem dialogovém okně](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) při použití [editoru dialogového okna](../windows/dialog-editor.md).

### <a name="activex-control"></a>Ovládací prvek ActiveX

Zobrazí seznam ovládacích prvků ActiveX. Vložení ovládacího prvku z tohoto dialogového okna negeneruje obálkovou třídu. Pokud potřebujete obálkovou třídu, použijte [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) si ji vytvořit (Další informace najdete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md)). Ovládací prvek ActiveX v tomto seznamu nezobrazí, zkuste nainstalovat ovládací prvek podle pokynů jeho dodavatele.

### <a name="path"></a>Cesta

Zobrazí soubor, ve kterém se nachází v ovládacím prvku ActiveX.

Můžete umístit ovládací prvky **nástrojů** okno pro snadný přístup. Další informace najdete v tématu [nástrojů](/visualstudio/ide/reference/).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Karta editoru dialogového okna, panel nástrojů](../windows/dialog-editor-tab-toolbox.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)