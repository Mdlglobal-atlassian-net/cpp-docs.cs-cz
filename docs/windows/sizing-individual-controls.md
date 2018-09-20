---
title: Změna velikosti jednotlivých ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9932b14b3d3afaa0afdff90c08ce44bf1f8648dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373457"
---
# <a name="sizing-individual-controls"></a>Změna velikosti jednotlivých ovládacích prvků

Použijte úchyty pro změnu velikosti ovládacího prvku. Pokud je ukazatel myši umístěn na úchyt pro změnu velikosti, změní tvar, který má označení směry, ve kterých můžete změnit velikost ovládacího prvku. Aktivní úchyty jsou pořádné; Pokud je dutý úchyt pro změnu velikosti, ovládací prvek nelze změnit velikost podél osy.

Můžete také změnit velikost ovládacího prvku pomocí přichycení vodítka a okraje ovládacího prvku, nebo přesunutím jeden přichycené zobrazení ovládacího prvku a Průvodce mimo jiné.

### <a name="to-size-a-control"></a>Pro nastavení velikosti ovládacího prvku

1. Vyberte ovládací prvek.

2. Přetažením úchytů změňte velikost ovládacího prvku:

   - Úchyty pro změnu velikosti na začátku a konce změnit velikost vodorovně nebo svisle.

   - Úchyty pro změnu velikosti v rozích změnit šířku a výšku.

   > [!TIP]
   > Můžete změnit velikost jednotky jeden dialogového okna ovládacího prvku (DLU) současně současným **Shift** klíče a pomocí **šipka vpravo** a **šipka dolů** klíče.

### <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Chcete-li automaticky velikost ovládacího prvku podle textu v rámci něj

1. Zvolte **velikost, aby se obsah** z **formátu** nabídky.

\- nebo –

- Klikněte pravým tlačítkem na ovládací prvek a vyberte **velikost obsahu** z místní nabídky.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)