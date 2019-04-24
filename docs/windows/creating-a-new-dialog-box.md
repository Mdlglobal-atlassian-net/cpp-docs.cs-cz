---
title: 'Postupy: Vytvoření dialogového okna (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: c5f026683881ba8e608bd00089879e0e2a7b4af2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223568"
---
# <a name="how-to-create-a-dialog-box-c"></a>Postupy: Vytvoření dialogového okna (C++)

Umístění a velikosti dialogového okna C++ a umístění a velikost ovládacích prvků na ní, se měří v jednotkách dialogového okna. Hodnoty jednotlivých ovládacích prvků a dialogové okno se zobrazí v pravém dolním rohu sady Visual Studio se na stavovém řádku při výběru.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Postupy

**Editoru dialogového okna** vám umožní:

### <a name="to-create-a-new-dialog-box"></a>K vytvoření nového dialogového okna

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na váš *.rc* a vyberte možnost **přidat prostředek**.

1. V **přidat prostředek** dialogu **dialogové okno** v **typ prostředku** seznamu a pak zvolte **nový**.

   Pokud symbol plus (**+**) se zobrazí vedle **dialogové okno** typ prostředku, znamená to, že pole šablon dialogového okna jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

   Otevře se dialogové okno Nový v **editoru dialogového okna**.

Můžete také otevřít stávající dialogových oknech v editoru dialogové okno pro úpravy.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Chcete-li vytvořit dialogové okno, které uživatel nemohou zavřít.

Můžete vytvořit modul runtime dialogové okno, které uživatel nemůže ukončeno. Tento druh dialogové okno je užitečný pro přihlášení a pro aplikace nebo dokumentu zámky.

1. V **vlastnosti** podokno pro dialogové okno, nastavte **systémové nabídky** vlastnost **false**.

   Toto nastavení zakáže nabídky systému dialogového a **Zavřít** tlačítko.

1. V dialogovém okně pole formuláře, odstraňte **zrušit** a **OK** tlačítka.

   V době běhu nemůže uživatel ukončit modální dialogové okno, které má tyto vlastnosti.

Pokud chcete povolit testování tohoto druhu dialogového okna, test dialog box – funkce zjistí při **Esc** stisknutí. **ESC** se také označuje jako virtuální vk_escape – klíč. Bez ohledu na to, jak je určen dialogovém okně chování za běhu, můžete testovací režim ukončit stisknutím kombinace kláves **Esc**.

> [!NOTE]
> Pro aplikace knihovny MFC, chcete-li vytvořit dialogové okno, které uživatelé nebudou moct zavřít, je nutné přepsat výchozí chování `OnOK` a `OnCancel` vzhledem k tomu, že i v případě, že odstraníte přidružené tlačítka, dialogové okno může stále vynechat stisknutím klávesy  **Zadejte** nebo **Esc**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>K určení umístění a velikosti dialogového okna

Existují vlastnosti můžete nastavit [okno vlastností](/visualstudio/ide/reference/properties-window) k určení, kde se zobrazí dialogové okno na obrazovce.

- Datový typ Boolean **Center** vlastnost.

   Pokud nastavíte hodnotu na **True**, dialogové okno se vždy zobrazí ve středu obrazovky. Pokud nastavíte tuto vlastnost na **False**, pak můžete nastavit **Pozice_x** a **Pozice_y** vlastnosti.

- **Pozice_x** a **Pozice_y** vlastnosti, které slouží k explicitnímu definování tam, kde na obrazovce se zobrazí dialogové okno.

   Tyto vlastnosti pozice jsou hodnoty posunu v levém horním rohu oblasti zobrazení, která je definována jako `{X=0, Y=0}`.

- **Absolutní zarovnání** vlastnost, která má vliv na pozici.

   Pokud **True**, souřadnice jsou relativní vzhledem k obrazovce. Pokud **False**, souřadnice jsou relativně k nadřazenému dialogovém oknu.

### <a name="to-test-a-dialog-box"></a>Testování dialogového okna

Při návrhu dialogového okna můžete simulovat a testovat jeho chování za běhu bez kompilace programu. V tomto režimu můžete:

- Zadejte text, vyberte ze seznamu pole se seznamem, zapnout nebo vypnout možnosti a volit příkazy.

- Otestujte pořadí ovládacích prvků.

- Otestujte seskupení ovládacích prvků, jako jsou přepínače a zaškrtávací políčka.

- Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.

> [!NOTE]
> Připojení ke kódu dialogového okna pomocí průvodců nejsou zahrnuta v simulaci.

Při testování dialogového okna se obvykle zobrazuje v umístění, které jsou relativní vůči hlavnímu oknu programu. Pokud jste tak nastavili dialogových oken **absolutní zarovnání** vlastnost **True**, zobrazí dialogové okno v pozici, která je relativní vzhledem k levého horního rohu obrazovky.

1. Když **editoru dialogového okna** aktivní okno, přejděte do nabídky **formátu** > **testovací dialogové okno**.

1. Chcete-li simulaci ukončit, stiskněte **Esc** nebo vyberte **Zavřít** tlačítko v dialogovém okně, kterou testujete.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Postupy: Správa ovládací prvky dialogového okna](../windows/controls-in-dialog-boxes.md)<br/>