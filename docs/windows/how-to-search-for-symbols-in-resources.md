---
title: 'Postupy: vyhledávání symbolů v prostředcích | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3aada3dac208fcf08a9b0e61ef822c3ab13b7b44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605763"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Postupy: Vyhledávání symbolů v prostředcích

### <a name="to-find-symbols-in-resources"></a>Chcete-li najít symboly v prostředcích

1. Z **upravit** nabídce zvolte **najít Symbol**.

2. V [dialogového okna Najít Symbol](http://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96)v **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte klíče akcelerátoru, které chcete najít (například ID_ACCEL1).

   > [!TIP]
   > Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) pro hledání, je nutné použít [najít v souborech – příkaz](/visualstudio/ide/reference/find-command) z **upravit** nabídky místo **najít Symbol**příkazu. Chcete-li regulární výrazy, musíte mít **použití: regulární výrazy** zaškrtnuto políčko v [dialogové okno hledání](http://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600). Pak kliknete tlačítko se šipkou vpravo na pravé straně **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.

3. Vyberte některou z **najít** možnosti.

4. Klikněte na tlačítko **najít další**.

   > [!NOTE]
   > Nelze hledat symboly v řetězci, akcelerátoru nebo binární prostředky.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem a [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)