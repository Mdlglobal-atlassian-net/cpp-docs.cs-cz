---
title: Editory prostředků (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: a752122d89b3d952aec664f0dec092af1599f143
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448915"
---
# <a name="resource-editors-c"></a>Editory prostředků (C++)

Editor prostředků je specializované prostředí pro vytváření nebo úprav prostředky, které jsou součástí projektu sady Visual Studio. Editory prostředků Visual Studio techniky a rozhraní vám pomůžou vytvářet a upravovat prostředky aplikace rychle a snadno sdílet. Editory prostředků umožňují zobrazit a upravit prostředky v příslušné prostředky editoru a ve verzi preview.

Otevře se editor odpovídající automaticky při vytvoření nebo otevření prostředku.

> [!NOTE]
> Protože spravované projekty nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [Editor obrázků](../windows/image-editor-for-icons.md) a [binární Editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

|Použití...|Chcete-li upravit...|
|----------------|----------------|
|[Editor akcelerátorů](../windows/accelerator-editor.md)|Tabulek akcelerátorů v aplikaci Visual Studio C++ projekty.|
|[Binární editor](binary-editor.md)|Informace o binárních dat a vlastních prostředků v projektech Visual C++, Visual Basic nebo Visual C#.|
|[Editor dialogových oken](../windows/dialog-editor.md)|Dialogová okna v sadě Visual Studio C++ projekty.|
|[Editor obrázků](../windows/image-editor-for-icons.md)|Rastrové obrázky, ikony, kurzory a další soubory obrázků v projektech Visual C++, Visual Basic nebo Visual C#.|
|[Editor nabídek](../windows/menu-editor.md)|Prostředky nabídky v sadě Visual Studio C++ projekty.|
|[Ribbon Editor](../mfc/ribbon-designer-mfc.md)|Prostředky z pásu karet v projektech knihovny MFC.|
|[Editor řetězce](../windows/string-editor.md)|Řetězec tabulky v sadě Visual Studio C++ projekty.|
|[Editor panelu nástrojů](../windows/toolbar-editor.md)|Prostředky panelu nástrojů v sadě Visual Studio C++ projekty. **Panelu nástrojů editoru** je součástí **Editor obrázků**.|
|[Editor informací o verzi](../windows/version-information-editor.md)|Informace o verzi v sadě Visual Studio C++ projekty.|

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [jak: Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Zobrazení a úpravy prostředků

Každý typ prostředku má editoru prostředků specifických pro příslušný typ prostředku. Můžete změnit uspořádání, změňte velikost, přidat ovládací prvky a funkce nebo jinak upravit aspektů prostředku pomocí editoru přidružené. Můžete také upravit prostředek v [textový formát](../windows/how-to-open-a-resource-script-file-in-text-format.md) a [binární formát](../windows/opening-a-resource-for-binary-editing.md).

Některé typy prostředků jsou jednotlivé soubory, které můžete importovat a používat různými způsoby; patří mezi ně rastrové obrázky, ikony, kurzory, panely nástrojů a soubory html. Tyto zdroje mají názvy souborů a [identifikátory prostředků](../windows/symbols-resource-identifiers.md). Jiné, jako je například dialogová okna, nabídek a tabulky řetězců v projekty Win32, existují pouze v rámci prostředku skriptů (.rc) souboru nebo souboru prostředků (.rct) šablony.

Prostředky může být také upravena mimo projekt bez nutnosti otevřít projekt, naleznete v tématu [jak: Vytvoření prostředků](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Vlastnosti prostředku může být upraveno pomocí **vlastnosti** okna.

- Chcete-li upravit vlastnosti prostředku, v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na prostředku, kterou chcete upravit a zvolte **vlastnosti**.  Potom v [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností prostředku.

- Pokud chcete vrátit zpět změny provedené na vlastnosti prostředku, ujistěte se, že váš prostředek má fokus **zobrazení prostředků** a zvolte **zpět** z **upravit** nabídky.

### <a name="win32-resources"></a>Prostředky Win32

Budete mít přístup k prostředkům Win32 v [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources) podokně.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Chcete-li zobrazit prostředek systému Win32 v editoru prostředků

1. Přejděte do nabídky **zobrazení** > **zobrazení prostředků**.

1. Pokud **zobrazení prostředků** okno nejsou nejvrchnější okna, vyberte **zobrazení prostředků** kartu a přenést ho do horní části.

1. Z **zobrazení prostředků**, rozbalte složku pro projekt, který obsahuje prostředky, které chcete zobrazit. Například pokud chcete zobrazit prostředku dialogového okna, rozbalte **dialogové okno** složky.

1. Dvakrát klikněte na prostředek, třeba **IDD_ABOUTBOX**.

   Prostředek se otevře ve vhodném editoru. Například pro prostředky dialogového okna, prostředek se otevře uvnitř **editoru dialogového okna**.

#### <a name="to-delete-an-existing-win32-resource"></a>Chcete-li odstranit existující prostředek systému Win32

1. V **zobrazení prostředků**, rozbalte uzel pro typ prostředku.

1. Klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit**.

> [!TIP]
> Tuto metodu můžete použít také v případě, že máte soubor .rc otevřený v okna dokumentu mimo projekt.

### <a name="managed-project-resources"></a>Spravovaný projekt prostředků

Protože spravovaných projektů nepoužívejte soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Použití [Editor obrázků](../windows/image-editor-for-icons.md) a [binární Editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky a editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

- Chcete-li zobrazit spravovaného prostředku v editoru prostředků v **Průzkumníka řešení**, dvakrát klikněte na prostředek, třeba *Bitmap1.bmp*, a prostředek se otevře ve vhodném editoru.

- Odstranění existujícího spravovaného prostředku, v **Průzkumníka řešení**, klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit**.

## <a name="preview-resources"></a>Náhled prostředků

Ve verzi Preview vašich prostředků, aby bylo možné zobrazit grafických prostředků bez jejich otevírání. V předběžné verzi je také užitečné pro spustitelné soubory po jste sestavili, protože identifikátory prostředků změnit na čísla. Protože tyto identifikátory číselné často neposkytuje dostatek informací, zobrazení náhledu prostředky vám pomůže rychle identifikovat.

Následující typy prostředků poskytují náhled rozložení vizuálu: Rastrový obrázek, dialogové okno, ikona, nabídka, kurzor, panel nástrojů

Následující prostředky neposkytují visual ve verzi preview: Akcelerátor, informace o verzi manifestu, tabulka řetězců

> [!NOTE]
> Náhled prostředků vyžaduje Win32.

### <a name="to-preview-resources"></a>Náhled prostředků

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources) nebo okno dokumentu, vyberte prostředek, třeba **IDD_ABOUTBOX**.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), vyberte **stránky vlastností** tlačítko.

   > [!TIP]
   > Použít zástupce, přejděte do nabídky **zobrazení** > **stránky vlastností**.

   **Vlastnost** pro prostředek se otevře stránka zobrazení ve verzi preview tohoto prostředku. Můžete použít **nahoru** a **dolů** v ovládacím prvku klávesy se šipkami přejdete strom **zobrazení prostředků** nebo okno dokumentu. **Vlastnost** stránky zůstávají otevřené, který se zobrazí jakémukoli prostředku, který má právě fokus a můžete zobrazit jejich náhled.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>