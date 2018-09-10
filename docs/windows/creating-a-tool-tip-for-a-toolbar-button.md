---
title: Vytvoření popisku tlačítka pro tlačítko panelu nástrojů (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e5fef71d3fa2ad76192a06603ed9e22d52eef71
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317820"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>Vytvoření popisku tlačítka pro tlačítko panelu nástrojů (C++)

### <a name="to-create-a-tool-tip"></a>Vytvoření popisku tlačítka

1. Vyberte tlačítko panelu nástrojů.

2. V [okno vlastností](/visualstudio/ide/reference/properties-window)v **výzvy** vlastnost pole, přidejte popis tlačítka pro stavový řádek; po něm, přidejte `\n` a název nástroje tip.

Je běžným příkladem popisku tlačítka **tisk** tlačítko **WordPad**:

1. Otevřít **WordPad**.

2. Najeďte myší **tisk** tlačítka panelu nástrojů.

3. Všimněte si, že slovo `Print` je nyní plovoucí pod ukazatele myši.

4. Podívejte se na stavovém řádku (dole velmi **WordPad** okno) – Všimněte si, že nyní zobrazuje text `Prints the active document`.

`Print` v **kroku 3** je "nástroj tip name," a `Prints the active document` z **kroku 4** je "Popis tlačítka na stavový řádek."

Pokud chcete tento efekt použití **nástrojů** editor, můžete nastavit **výzvy** vlastnost `Prints the active document\nPrint`.

> [!NOTE]
> Můžete upravit pomocí text výzvy [okno vlastností](/visualstudio/ide/reference/properties-window).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Vytváření, přesunutí a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Editor panelu nástrojů](../windows/toolbar-editor.md)