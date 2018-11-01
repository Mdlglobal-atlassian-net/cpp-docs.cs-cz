---
title: Přesunutí řetězce z jednoho zdrojového souboru do jiného (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
ms.openlocfilehash: e89a0d44dc824c72710f8a047a18771ba8da492b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649810"
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

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Přizpůsobení rozložení oken](/visualstudio/ide/customizing-window-layouts-in-visual-studio)