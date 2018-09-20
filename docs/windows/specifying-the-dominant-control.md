---
title: Určení dominantního ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog Editor [C++], dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31bb19a0854bd28573d474a65781808eaecd7ce2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407566"
---
# <a name="specifying-the-dominant-control"></a>Určení dominantního ovládacího prvku

Ovládací prvek je nejprve dominantního ovládacího prvku.

### <a name="to-specify-the-dominant-control"></a>K určení dominantního ovládacího prvku

1. Podržte stisknutou klávesu **Ctrl** key a klikněte na ovládací prvek, který chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*.

   **Poznámka:** úchyty dominantního ovládacího prvku jsou pořádné popisovače podřízených ovládacích prvků, které jsou prázdné. Všechny další změny velikosti nebo zarovnání podle dominantního ovládacího prvku.

### <a name="to-change-the-dominant-control"></a>Chcete-li změnit dominantního ovládacího prvku

1. Zrušte aktuální výběr kliknutím mimo všechny aktuálně vybrané ovládací prvky.

2. Opakujte předchozí postup nejprve výběr jiného ovládacího prvku.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Výběr více ovládacích prvků](../windows/selecting-multiple-controls.md)<br/>
[Výběr ovládacích prvků](../windows/selecting-controls.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)