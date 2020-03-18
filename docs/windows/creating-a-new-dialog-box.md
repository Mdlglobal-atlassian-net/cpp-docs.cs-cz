---
title: 'Postupy: Vytvoření dialogového okna (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 380cf58180913f538c1c326d6aaf49947b694063
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445414"
---
# <a name="how-to-create-a-dialog-box-c"></a>Postupy: Vytvoření dialogového okna (C++)

Umístění a velikost C++ dialogového okna a umístění a velikost ovládacích prvků v něm jsou měřeny v jednotkách dialogu. Hodnoty pro jednotlivé ovládací prvky a dialogové okno se zobrazí v pravém dolním rohu stavového řádku sady Visual Studio při jejich výběru.

> [!NOTE]
> Pokud projekt ještě neobsahuje soubor. RC, přečtěte si téma [Vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Postup

**Editor dialogových oken** vám umožní:

### <a name="to-create-a-new-dialog-box"></a>Vytvoření nového dialogového okna

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem myši na soubor *. RC* a vyberte **Přidat prostředek**.

1. V dialogovém okně **Přidat prostředek** vyberte v seznamu **typ prostředku** možnost **dialog** a pak zvolte možnost **Nový**.

   Pokud se vedle typu prostředku **dialogového okna** objeví znaménko plus ( **+** ), znamená to, že jsou k dispozici šablony dialogových oken. Vyberte znaménko plus a rozbalte seznam šablon, vyberte šablonu a zvolte **Nový**.

   Nové dialogové okno se otevře v **editoru dialogového okna**.

V editoru dialogových oken můžete také otevřít existující dialogová okna pro úpravy.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Vytvoření dialogového okna, které uživatel nemůže ukončit

Můžete vytvořit dialogové okno runtime, které uživatel nemůže ukončit. Tento druh dialogového okna je vhodný pro přihlášení a pro zámky aplikací nebo dokumentů.

1. V podokně **vlastnosti** dialogového okna nastavte vlastnost **systémová nabídka** na **hodnotu NEPRAVDA**.

   Toto nastavení zakáže systémovou nabídku a tlačítko **Zavřít** dialogového okna.

1. Ve formuláři dialogového okna odstraňte tlačítka **Storno** a **OK** .

   V době spuštění nemůže uživatel ukončit modální dialogové okno s těmito charakteristikami.

Chcete-li povolit testování tohoto druhu dialogového okna, funkce dialogového okna test detekuje při stisknutí **klávesy ESC** . **Klávesa ESC** je také známá jako VK_ESCAPE virtuální klíč. Bez ohledu na to, jak je dialogové okno navrženo v době běhu, můžete ukončit režim testu stisknutím klávesy **ESC**.

> [!NOTE]
> Pro aplikace MFC, chcete-li vytvořit dialogové okno, které uživatel nemůže ukončit, je nutné přepsat výchozí chování `OnOK` a `OnCancel`, protože i když odstraníte přidružená tlačítka, dialogové okno může být stále zavřeno stisknutím klávesy **ENTER** nebo **ESC**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Určení umístění a velikosti dialogového okna

V [okně Vlastnosti](/visualstudio/ide/reference/properties-window) lze nastavit vlastnosti, které určují, kde se zobrazí dialogové okno na obrazovce.

- Vlastnost logického **středu** .

   Pokud nastavíte hodnotu na **true**, dialogové okno se vždy zobrazí ve středu obrazovky. Pokud nastavíte tuto vlastnost na **hodnotu false**, můžete nastavit vlastnosti **XPos** a **YPos** .

- Vlastnosti **XPos** a **YPos** , které se používají k explicitnímu definování, kde se zobrazí dialogové okno na obrazovce.

   Tyto vlastnosti pozice jsou odsazené hodnoty z levého horního rohu oblasti zobrazení, která je definována jako `{X=0, Y=0}`.

- **Absolutní vlastnost align** , která má vliv na pozici.

   Při **hodnotě true**jsou souřadnice relativní vzhledem k obrazovce. Pokud je **hodnota false**, souřadnice jsou relativní vzhledem k oknu vlastníka dialogového okna.

### <a name="to-test-a-dialog-box"></a>Testování dialogového okna

Při navrhování dialogového okna můžete simulovat a testovat jeho chování za běhu bez kompilování programu. V tomto režimu můžete:

- Zadejte text, vyberte ze seznamu pole se seznamem, zapněte nebo vypněte možnosti a zvolte příkazy.

- Otestujte pořadí ovládacích prvků.

- Otestujte seskupení ovládacích prvků, jako jsou například přepínače a zaškrtávací políčka.

- Otestujte klávesové zkratky pro ovládací prvky v dialogovém okně.

> [!NOTE]
> V simulaci nejsou zahrnuta připojení k kódu dialogového okna vytvořenému pomocí průvodců.

Když otestujete dialogové okno, obvykle se zobrazí v umístění, které je relativní vzhledem k hlavnímu oknu programu. Pokud jste nastavili vlastnost **absolutní zarovnání** dialogového okna na **hodnotu true**, zobrazí se dialogové okno na pozici, která je relativní vzhledem k levému hornímu rohu obrazovky.

1. Když je **Editor dialogového okna** aktivní okno, přejděte do nabídky **Format** > **dialog test**.

1. Chcete-li ukončit simulaci, stiskněte klávesu **ESC** nebo vyberte tlačítko **Zavřít** v dialogovém okně, které testujete.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor dialogových oken](../windows/dialog-editor.md)<br/>
[Postupy: Správa ovládacích prvků dialogového okna](../windows/controls-in-dialog-boxes.md)<br/>