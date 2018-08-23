---
title: Přidání informací o verzi pro jiný jazyk | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- languages, version information
- New Version Info Block
- blocks, adding
- resources [Visual Studio], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db11dee47b51cf695a93489d4ab851be47c39144
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612655"
---
# <a name="adding-version-information-for-another-language"></a>Přidání informací o verzi pro jiný jazyk

### <a name="to-add-version-information-for-another-language-new-info-block"></a>Chcete-li přidat informace o verzi pro jiný jazyk (nový blok informací o)

1. Otevřete poklepáním v prostředku informací o verzi [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Klikněte pravým tlačítkem v tabulce informace o verzi a zvolte **novou verzi informačního bloku** z místní nabídky.

   Tento příkaz přidá do aktuálního prostředku informací o verzi z bloku Další informace a otevře se jeho odpovídající vlastnosti v [okno vlastností](/visualstudio/ide/reference/properties-window).

3. V **vlastnosti** okno, vyberte příslušný jazyk a znakové sady pro nový blok.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor informací o verzi](../windows/version-information-editor.md)  
[Informace o verzi (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)