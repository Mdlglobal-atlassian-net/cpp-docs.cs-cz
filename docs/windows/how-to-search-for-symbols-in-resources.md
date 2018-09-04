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
ms.openlocfilehash: 5cefedc4b1517b242eef62192e8d03a60097700c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683169"
---
# <a name="how-to-search-for-symbols-in-resources"></a>Postupy: Vyhledávání symbolů v prostředcích

### <a name="to-find-symbols-in-resources"></a>Chcete-li najít symboly v prostředcích

1. Z **upravit** nabídce zvolte **najít Symbol**.

2. V [dialogového okna Najít Symbol](/visualstudio/ide/go-to)v **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte klíče akcelerátoru, které chcete najít (například ID_ACCEL1).

   > [!TIP]
   > Použití [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) pro hledání, je nutné použít [najít v souborech – příkaz](/visualstudio/ide/reference/find-command) z **upravit** nabídky místo **najít Symbol**příkazu. Chcete-li regulární výrazy, musíte mít **použití: regulární výrazy** zaškrtnuto políčko v [dialogové okno hledání](/visualstudio/ide/finding-and-replacing-text). Pak kliknete tlačítko se šipkou vpravo na pravé straně **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole.

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