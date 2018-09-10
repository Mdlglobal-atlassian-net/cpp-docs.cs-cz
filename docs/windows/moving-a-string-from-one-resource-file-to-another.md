---
title: Přesunutí řetězce z jednoho zdrojového souboru do jiného (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c99b5640d2ea855ade7f3f39ba233b3e5ff2ef04
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318860"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>Přesunutí řetězce z jednoho zdrojového souboru do jiného (C++)

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Přesunutí řetězce z jednoho zdrojového souboru skriptu na jiný

1. V obou souborů RC otevřete tabulky řetězců. (Další informace najdete v tématu [zobrazování prostředků v prostředků skriptu souboru mimo of projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Klikněte pravým tlačítkem na řetězec, který chcete přesunout a zvolte **Vyjmout** z místní nabídky.

3. Umístěte kurzor na cíli **Editor řetězců** okna.

4. V souboru .rc, do kterého chcete přesunout řetězec, klikněte pravým tlačítkem a zvolte **vložit** z místní nabídky.

   > [!NOTE]
   > Pokud **ID** nebo **hodnotu** přesunutý řetězec konfliktů s existujícím **ID** nebo **hodnotu** v cílovém souboru a buď **ID** nebo **hodnotu** změn přesunutý řetězec. Pokud řetězec existuje se stejným **ID**, **ID** změn přesunutý řetězec. Pokud řetězec existuje se stejným **hodnotu**, **hodnotu** změn přesunutý řetězec.

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)  