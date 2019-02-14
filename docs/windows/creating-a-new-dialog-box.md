---
title: Vytvoření dialogového okna (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: a3b8143d3a70906f910a445816a188913a593e5d
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264813"
---
# <a name="creating-a-dialog-box-c"></a>Vytvoření dialogového okna (C++)

Umístění a velikosti dialogového okna C++ a umístění a velikost ovládacích prvků na ní, se měří v jednotkách dialogového okna. Hodnoty jednotlivých ovládacích prvků a dialogové okno se zobrazí v pravém dolním rohu sady Visual Studio se na stavovém řádku při výběru.

Při návrhu dialogového okna, můžete také simulovat a testovat jeho chování za běhu bez kompilace programu. V tomto režimu můžete:

- Zadejte text, vyberte ze seznamu pole se seznamem, zapnout nebo vypnout možnosti a volit příkazy.

- Otestujte pořadí ovládacích prvků.

- Otestujte seskupení ovládacích prvků, jako jsou přepínače a zaškrtávací políčka.

- Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.

   > [!NOTE]
   > Připojení ke kódu dialogového okna pomocí průvodců nejsou zahrnuta v simulaci.

Při testování dialogového okna se obvykle zobrazuje v umístění, které jsou relativní vůči hlavnímu oknu programu. Pokud jste nastavili v dialogovém okně **absolutní zarovnání** vlastnost **True**, zobrazí se dialogové okno v pozici, která je relativní vzhledem k levého horního rohu obrazovky.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>K vytvoření nového dialogového okna

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **přidat prostředek** z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V **přidat prostředek** dialogu **dialogové okno** v **typ prostředku** seznamu a pak zvolte **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **dialogové okno** typ prostředku, znamená to, že pole šablon dialogového okna jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

   Otevře se dialogové okno Nový v **dialogové okno** editoru.

   Můžete také [otevřete existující dialogových oknech v editoru dialogové okno pro úpravy](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Chcete-li vytvořit dialogové okno, které uživatel nemohou zavřít.

Můžete vytvořit modul runtime dialogové okno, které uživatel nemůže ukončeno. Tento druh dialogové okno je užitečný pro přihlášení a pro aplikace nebo dokumentu zámky.

1. V **vlastnosti** podokno pro dialogové okno, nastavte **systémové nabídky** vlastnost **false**.

   Toto nastavení zakáže nabídky systému dialogového a **Zavřít** tlačítko.

1. V dialogovém okně pole formuláře, odstraňte **zrušit** a **OK** tlačítka.

   V době běhu nemůže uživatel ukončit modální dialogové okno, které má tyto vlastnosti.

Pokud chcete povolit testování tohoto druhu dialogového okna, test dialog box – funkce zjistí při **Esc** stisknutí. (**Esc** se také označuje jako virtuální vk_escape – klíč.) Bez ohledu na to, jak je určen dialogovém okně chování za běhu, můžete testovací režim ukončit stisknutím kombinace kláves **Esc**.

> [!NOTE]
> Pro aplikace knihovny MFC, chcete-li vytvořit dialogové okno, které uživatelé nebudou moct zavřít, je nutné přepsat výchozí chování `OnOK` a `OnCancel` vzhledem k tomu, že i v případě, že odstraníte přidružené tlačítka, dialogové okno může stále vynechat stisknutím klávesy  **Zadejte** nebo **Esc**.

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>K určení umístění a velikosti dialogového okna

Existují tři vlastnosti, které můžete nastavit [okno vlastností](/visualstudio/ide/reference/properties-window) k určení, kde se zobrazí dialogové okno na obrazovce. **Center** vlastnost je logická hodnota, pokud hodnotu nastavíte na **True**, dialogové okno se vždy zobrazí ve středu obrazovky. Pokud ji nastavíte na **False**, pak můžete nastavit **Pozice_x** a **Pozice_y** explicitně definované tam, kde na obrazovce se zobrazí dialogové okno Vlastnosti. Jsou vlastnosti pozici posunutí hodnoty v levém horním rohu oblasti zobrazení, která je definována jako `{X=0, Y=0}`. Pozice je taky založený na **absolutní zarovnání** vlastnost: Pokud **True**, souřadnice jsou relativní vzhledem k obrazovce; Pokud **False**, souřadnice jsou relativní vzhledem k dialogového okna okno vlastníka.

## <a name="to-test-a-dialog-box"></a>Testování dialogového okna

1. Když **dialogové okno** editor není aktivní okno na řádku nabídek, zvolte **formátu** > **testovací dialogové okno**.

1. Chcete-li simulaci ukončit, stiskněte **Esc**, nebo prostě vybrat **Zavřít** tlačítko v dialogovém okně, kterou testujete.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Postupy: Vytvoření prostředku](../windows/how-to-create-a-resource.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)<br/>