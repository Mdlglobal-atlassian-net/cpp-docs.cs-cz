---
title: 'Postupy: vytvoření souboru skriptu prostředků (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32258a05cade33f20546acfc02b98370ada2b073
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387130"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Postupy: vytvoření souboru skriptu prostředků (C++)

> [!NOTE]
> **Editor prostředků** není k dispozici ve verzích Express.
>
> Tento materiál se vztahuje na aplikace klasické pracovní plochy Windows. Projekty v jazycích technologie .NET nepoužívají soubory skriptu prostředků. Zobrazit [soubory prostředků](../windows/resource-files-visual-studio.md), další informace.

### <a name="to-create-a-new-resource-script-rc-file"></a>Vytvoření nového souboru skriptu prostředků (.rc)

1. Přesuňte fokus na složku existujícího projektu v **Průzkumníka řešení**, například `MyProject`.

   > [!NOTE]
   > Nepleťte si složku projektu se složkou řešení v **Průzkumníka řešení**. Pokud přesunete fokus na **řešení** složka, budou možnosti v **přidat novou položku** dialogové okno (v kroku 3) se bude lišit.

2. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.

3. V **přidat novou položku** dialogové okno, klikněte na tlačítko **Visual C++** složky klikněte na tlačítko **soubor prostředků (.rc)** v pravém podokně.

4. Zadejte název souboru skriptu prostředku v **název** textové pole a potom klikněte na **otevřít**.

Teď můžete [vytvořit](../windows/how-to-create-a-resource.md) a přidejte nové prostředky do souboru .rc.

> [!NOTE]
> Skript prostředků (soubor .rc) lze přidat pouze do existujícího projektu, který je načten do vývojového prostředí (IDE) pro Visual Studio. Nelze vytvořit samostatný soubor .rc (mimo projekt). [Šablony prostředků](../windows/how-to-use-resource-templates.md) (soubory .rct) lze vytvořit kdykoli.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)