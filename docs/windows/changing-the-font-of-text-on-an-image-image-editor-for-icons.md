---
title: Změna písma textu obrázku (editor obrázků pro ikony)
ms.date: 11/04/2016
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
ms.openlocfilehash: 2bbd8096a2957099acc8c06d501f3ad407b9a974
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495521"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Změna písma textu obrázku (editor obrázků pro ikony)

Následující postup je příklad toho, jak:

- Přidejte text do ikony v aplikaci Windows

- Manipulace s písma textu

### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku

1. Vytvoření aplikace C++ Windows Forms. Podrobnosti najdete v tématu [vytvoření projektu aplikace Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). `app.ico` Ve výchozím nastavení se přidá do projektu soubor.

2. V **Průzkumníka řešení**, poklikejte na soubor app.ico. [Editor obrázků](../windows/image-editor-for-icons.md) se otevře.

3. Z **Image** nabídce vyberte možnost **nástroje** a pak vyberte **textový nástroj**. [Dialogové okno textový nástroj](../windows/text-tool-dialog-box-image-editor-for-icons.md) se zobrazí.

4. V **textový nástroj** dialogovém okně `C++` v oblasti prázdný text. Tento text se zobrazí v okně možností změny velikosti se nachází v levém horním rohu `app.ico`v **Editor obrázků**.

5. V **Editor obrázků**, přetáhněte pole umožňující změnu velikosti na střed app.ico, aby se zlepšila čitelnost textu.

6. V **textový nástroj** dialogové okno, klikněte na tlačítko **písmo** tlačítko. [Dialogové okno písmo textového nástroje](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) se zobrazí.

7. V **písmo nástroje Text** dialogu **časy New Roman** ze seznamu dostupných písem, které jsou uvedeny v **písmo** pole se seznamem.

8. Vyberte **tučné** ze seznamu styly dostupné písmo, které jsou uvedené v **styl písma** pole se seznamem.

9. Vyberte **10** ze seznamu dostupných bodů velikosti uvedené v **velikost** pole se seznamem.

10. Klikněte na tlačítko **OK** tlačítko. **Písmo nástroje Text** dialogové okno se zavře a použije se nové nastavení písma v textu.

11. Klikněte na tlačítko **Zavřít** tlačítko **textový nástroj** dialogové okno. Pole umožňující změnu velikosti celého textu zmizí z **Editor obrázků**.

## <a name="see-also"></a>Viz také

[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Panel nástrojů](../windows/toolbar-image-editor-for-icons.md)