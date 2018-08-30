---
title: Změna písma textu obrázku (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a8f06ae0021a95e9b4ae40506cfc91d6a8ae99b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200811"
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Změna písma textu obrázku (editor obrázků pro ikony)

Následující postup je příklad toho, jak:

- Přidejte text do ikony v aplikaci Windows

- Manipulace s písma textu

### <a name="to-change-the-font-of-text-on-an-image"></a>Změna písma textu obrázku

1. Vytvoření aplikace C++ Windows Forms. Podrobnosti najdete v tématu [vytvoření projektu aplikace Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5\(v=vs.100\)). [Šablony aplikace Windows Forms](https://msdn.microsoft.com/1babdebf-ab3f-4a64-a608-98499a5b9cea) přidá soubor s názvem `app.ico` do svého projektu ve výchozím nastavení.

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

[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Panel nástrojů](../windows/toolbar-image-editor-for-icons.md)