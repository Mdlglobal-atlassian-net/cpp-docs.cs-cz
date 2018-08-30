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
ms.openlocfilehash: f105f41c465d2750d372a8794a9ab66fa13db466
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215979"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Postupy: Vyhledávání symbolů v prostředcích

### <a name="to-find-symbols-in-resources"></a>Chcete-li najít symboly v prostředcích

1. Z **upravit** nabídce zvolte **najít Symbol**.

2. V [dialogového okna Najít Symbol](https://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96)v **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte klíče akcelerátoru, které chcete najít (například ID_ACCEL1).

   > [!TIP]
   > Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) pro hledání, je nutné použít [najít v souborech – příkaz](/visualstudio/ide/reference/find-command) z **upravit** nabídky místo **najít Symbol**příkazu. Chcete-li regulární výrazy, musíte mít **použití: regulární výrazy** zaškrtnuto políčko v [dialogové okno hledání](https://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600). Pak kliknete tlačítko se šipkou vpravo na pravé straně **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.

3. Vyberte některou z **najít** možnosti.

4. Klikněte na tlačítko **najít další**.

   > [!NOTE]
   > Nelze hledat symboly v řetězci, akcelerátoru nebo binární prostředky.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům zobrazení statických prostředků a přiřazování prostředků řetězců pro vlastnosti.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)