---
title: Jak najít prostředek řetězce (C++) | Dokumentace Microsoftu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
ms.openlocfilehash: 0e6d8ac8027028377e903a9e0a3c89238a9862a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585920"
---
# <a name="finding-a-string-resource-c"></a>Jak najít prostředek řetězce (C++)

Můžete vyhledat jeden nebo více řetězců v tabulce řetězců a použít [regulární výrazy](/visualstudio/ide/using-regular-expressions-in-visual-studio) s **najít v souborech** příkazu (**upravit** nabídky) najít všechny instance řetězce které odpovídají vzoru.

### <a name="to-find-a-string-in-the-string-table"></a>K vyhledání řetězce v tabulce řetězců

1. Otevřete poklepáním na ikonu v tabulce řetězců [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Na **upravit** nabídky, klikněte na tlačítko **najít a nahradit**, klikněte na tlačítko **najít**.

3. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte titulek identifikátor textu nebo prostředku řetězce, které chcete najít.

4. Vyberte některou z **najít** možnosti.

5. Klikněte na tlačítko **najít další**.

   > [!TIP]
   > Chcete-li použít regulární výrazy při vyhledávání souborů, použijte **najít v souborech** příkazu. Zadejte regulární výraz k porovnání vzoru, nebo klikněte na tlačítko napravo **najít** pole k zobrazení seznamu hledání regulárních výrazů. Když vyberete výrazu z tohoto seznamu, je nahrazen jako hledaný text v **najít** pole. Pokud používáte regulární výrazy, je nutné **použití: regulární výrazy** je zaškrtnuto políčko.

Informace o přidávání prostředků do spravovaných projektů (těch, které se zaměřují na modul common language runtime), najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [návod: lokalizace Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor řetězce](../windows/string-editor.md)