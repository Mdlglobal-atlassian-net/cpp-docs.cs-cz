---
title: Změna pořadí karet ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5f846244956687b73b6fc7272fe0c4d7d00d0e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596338"
---
# <a name="changing-the-tab-order-of-controls"></a>Změna pořadí karet ovládacích prvků

Pořadí, ve kterém je pořadí **kartu** klíč přesune zaměření pro vstup z jednoho ovládacího prvku v rámci dialogového okna. Obvykle pokračuje pořadí zleva doprava a shora dolů v dialogovém okně. Každý ovládací prvek má **Tabstop** vlastnost, která určuje, zda ovládací prvek nastaven vstupní fokus.

### <a name="to-set-input-focus-for-a-control"></a>Chcete-li nastavit fokus vstupu pro ovládací prvek

1. V [okno vlastností](/visualstudio/ide/reference/properties-window)vyberte **True** nebo **False** v **Tabstop** vlastnost.

Dokonce i ovládací prvky, které nemají **Tabstop** vlastnost nastavena na hodnotu **True** musí být součástí pořadí. To může být důležité, například, když jste [definujte přístupové klíče (klávesových zkratek)](../windows/defining-mnemonics-access-keys.md) pro ovládací prvky, které nemají titulky. Statický text, který obsahuje přístupový klíč pro související ovládací prvek musí bezprostředně předcházet související ovládací prvek v pořadí.

> [!NOTE]
> Pokud vaše dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob, jakým se zobrazí ovládací prvky. Ovládací prvky, které jsou dále v pořadí karet se vždy zobrazují nad překrývající se ovládací prvky, které předcházet v pořadí.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li zobrazit aktuální pořadí pro všechny ovládací prvky v dialogovém okně

1. Na **formátu** nabídky, klikněte na tlačítko **pořadí**.

\- nebo –

- Stisknutím klávesy **Ctrl**+**D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li změnit pořadí ovládacích prvků pro všechny ovládací prvky v dialogovém okně

1. Na **formátu** nabídky, klikněte na tlačítko **pořadí**.

   Řadu každý ovládací prvek v levém horním rohu se zobrazí místo něj v aktuální pořadí.

2. Nastavení pořadí karet klikněte na každý prvek v pořadí, které chcete **kartu** klíč použít.

3. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

   > [!TIP]
   > Jakmile zadáte **pořadí** režimu, můžete stisknout **Esc** nebo **Enter** zakázat možnost změnit pořadí ovládacích prvků.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Chcete-li změnit pořadí pro dva nebo více ovládacích prvků

1. Z **formátu** nabídce zvolte **pořadí**.

2. Zadejte, kde se začne změna v pořadí. Chcete-li to provést, podržte **Ctrl** key a klikněte na ovládací prvek před ten, kde chcete začít změněné směr.

   Například, pokud chcete změnit pořadí ovládacích prvků `7` prostřednictvím `9`, podržte stisknutou klávesu **Ctrl**, vyberte ovládací prvek `6` první.

   > [!NOTE]
   > Chcete-li nastavit konkrétní ovládací prvek na číslo `1` (první v pořadí), poklepejte na ovládací prvek.

3. Verze **Ctrl** klíče a pak klikněte na ovládací prvky v pořadí, které chcete **kartu** klíč dodržovat od tohoto okamžiku.

4. Stisknutím klávesy **Enter** ukončíte **pořadí** režimu.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Ovládací prvky](../mfc/controls-mfc.md)