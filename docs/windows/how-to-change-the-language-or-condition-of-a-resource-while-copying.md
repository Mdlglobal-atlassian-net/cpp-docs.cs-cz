---
title: 'Postupy: Změna jazyka nebo podmínky prostředku během kopírování (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property [C++]
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6239acd275d94eb2a59fe59882095d5106d3fc1e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405733"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Postupy: Změna jazyka nebo podmínky prostředku během kopírování (C++)

Při kopírování v prostředku, můžete změnit jeho vlastnost jazyka vlastnost podmínka nebo obojí.

- Určuje jazyk prostředku přesně to, jazyk prostředku. Toto je používáno [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) vám pomůže identifikovat prostředek, pro který potřebujete. (Ale prostředků může mít rozdíly pro každý jazyk, který nesouvisí se text, například akcelerátory, které může fungovat jenom na použití japonské klávesnice nebo rastrový obrázek, který může být pouze vhodné pro čínštinu lokalizované sestavení atd.)

- Podmínky prostředku je definovaný symbol, který určuje podmínku, pod kterým se má použít tento konkrétní kopie prostředku.

Jazyk a podmínky prostředku jsou uvedeny v závorkách za názvem prostředku v okně pracovního prostoru. V tomto příkladu používá prostředek s názvem IDD_AboutBox finština jako svůj jazyk a jeho stav je XX33.

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Kopírovat existující prostředek a změnit jeho jazyka nebo podmínky

1. V souboru .rc nebo v [zobrazení prostředků](../windows/resource-view-window.md) okna, klikněte pravým tlačítkem na prostředek, které chcete kopírovat.

2. Zvolte **vložit kopii** z místní nabídky.

3. V **vložit kopii prostředku** dialogové okno:

   - Pro **jazyk** seznamu, vyberte jazyk.

   - V **podmínku** zadejte podmínku.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Kopírování prostředků](../windows/how-to-copy-resources.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)