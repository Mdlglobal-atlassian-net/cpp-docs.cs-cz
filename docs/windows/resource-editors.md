---
title: Editory prostředkůC++()
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
ms.openlocfilehash: 5f12b126db7c0e040f06640d3ecd201007d73968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167885"
---
# <a name="resource-editors-c"></a>Editory prostředkůC++()

Editor prostředků je specializované prostředí pro vytváření a úpravu prostředků, které jsou součástí projektu sady Visual Studio. Editory prostředků sady Visual Studio sdílí techniky a rozhraní, které vám pomůžou rychle a snadno vytvářet a upravovat prostředky aplikace. Editory prostředků umožňují zobrazit a upravit prostředky v příslušných editorech a v prostředcích Preview.

Vhodný Editor se automaticky otevře při vytváření nebo otevírání prostředku.

> [!NOTE]
> Vzhledem k tomu, že spravované projekty nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumník řešení**. Můžete použít [Editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

|Použijte...|Chcete upravit...|
|----------------|----------------|
|[Editor akcelerátorů](../windows/accelerator-editor.md)|Tabulky akcelerátorů v projektech C++ sady Visual Studio.|
|[Binární editor](binary-editor.md)|Informace o binárních datech a vlastní prostředky C++v projektech visual, Visual Basic C# nebo Visual.|
|[Editor dialogových oken](../windows/dialog-editor.md)|Dialogová okna v projektech C++ sady Visual Studio.|
|[Editor obrázků](../windows/image-editor-for-icons.md)|Rastrové obrázky, ikony, kurzory a další soubory obrázků v projektech C++visual, Visual Basic nebo Visual C# .|
|[Editor nabídek](../windows/menu-editor.md)|Prostředky nabídky v projektech sady C++ Visual Studio.|
|[Editor pásu karet](../mfc/ribbon-designer-mfc.md)|Prostředky pásu karet v projektech MFC.|
|[Editor řetězce](../windows/string-editor.md)|Tabulky řetězců v projektech sady C++ Visual Studio.|
|[Editor panelu nástrojů](../windows/toolbar-editor.md)|Prostředky panelu nástrojů v projektech C++ sady Visual Studio. **Editor panelu nástrojů** je součástí **editoru obrázků**.|
|[Editor informací o verzi](../windows/version-information-editor.md)|Informace o verzi v projektech C++ sady Visual Studio.|

> [!NOTE]
> Pokud projekt ještě neobsahuje soubor. RC, přečtěte si téma [Postupy: vytváření prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Zobrazení a úprava prostředků

Každý typ prostředku má editor prostředků specifický pro daný typ prostředku. Můžete změnit uspořádání, změnit velikost, přidat ovládací prvky a funkce nebo jinak upravit aspekty prostředku pomocí přidruženého editoru. Prostředek můžete také upravit v [textovém formátu](../windows/how-to-open-a-resource-script-file-in-text-format.md) a v [binárním formátu](../windows/opening-a-resource-for-binary-editing.md).

Některé typy prostředků jsou jednotlivé soubory, které je možné naimportovat a používat různými způsoby. mezi ně patří rastrové obrázky, ikony, kurzory, panely nástrojů a soubory HTML. Tyto prostředky mají názvy souborů a [identifikátorů prostředků](../windows/symbols-resource-identifiers.md). Ostatní, například dialogy, nabídky a tabulky řetězců v projektech Win32, existují pouze jako součást souboru skriptu prostředků (. RC) nebo šablony prostředků (. RCT).

Prostředky je také možné upravovat mimo projekt, aniž by byl projekt otevřený, viz [Postupy: vytváření prostředků](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Vlastnosti prostředku lze upravit pomocí okna **vlastnosti** .

- Chcete-li upravit vlastnosti prostředku, klikněte v [prostředky](how-to-create-a-resource-script-file.md#create-resources)pravým tlačítkem myši na prostředek, který chcete upravit, a vyberte možnost **vlastnosti**.  Pak v [okno Vlastnosti](/visualstudio/ide/reference/properties-window)změňte vlastnosti prostředku.

- Pokud chcete vrátit zpět změnu vlastností prostředku, ujistěte se, že se váš prostředek zaměřuje na **prostředky** a v nabídce **Upravit** vyberte **zpět** .

### <a name="win32-resources"></a>Prostředky Win32

K prostředkům Win32 získáte přístup v podokně [prostředky](how-to-create-a-resource-script-file.md#create-resources) .

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Zobrazení prostředku Win32 v editoru prostředků

1. Přejít na **zobrazení** nabídky > **jiných** > Windows **prostředky**.

1. Pokud okno **prostředky** není horním největším oknem, vyberte kartu **prostředky** a přeneste ji do horní části.

1. Z **prostředky**rozbalte složku projektu obsahující prostředky, které chcete zobrazit. Například pokud chcete zobrazit prostředek dialogového okna, rozbalte složku **dialogového okna** .

1. Dvakrát klikněte na prostředek, například **IDD_ABOUTBOX**.

   Prostředek se otevře ve vhodném editoru. Například pro prostředky dialogového okna se prostředek otevře v **editoru dialogového okna**.

#### <a name="to-delete-an-existing-win32-resource"></a>Odstranění existujícího prostředku Win32

1. V **prostředky**rozbalte uzel pro typ prostředku.

1. Klikněte pravým tlačítkem na prostředek, který chcete odstranit, a vyberte **Odstranit**.

> [!TIP]
> Tuto metodu lze použít také v případě, že je soubor. RC otevřen v okně dokumentu mimo projekt.

### <a name="managed-project-resources"></a>Spravované prostředky projektu

Vzhledem k tomu, že spravované projekty nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumník řešení**. Použijte [Editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky a editory prostředků sady Visual Studio nepodporují úpravu integrovaných prostředků.

- Chcete-li zobrazit spravovaný prostředek v editoru prostředků, v **Průzkumník řešení**dvakrát klikněte na prostředek, například *Bitmap1. bmp*a prostředek se otevře v příslušném editoru.

- Pokud chcete odstranit existující spravovaný prostředek, klikněte v **Průzkumník řešení**pravým tlačítkem na prostředek, který chcete odstranit, a vyberte **Odstranit**.

## <a name="preview-resources"></a>Náhled prostředků

Zobrazte náhled prostředků, abyste mohli zobrazit grafické prostředky bez nutnosti jejich otevírání. Náhled je vhodný také pro spustitelné soubory po jejich kompilování, protože se identifikátory prostředků změnily na čísla. Vzhledem k tomu, že tyto číselné identifikátory často neposkytují dostatek informací, vám jejich náhled pomůže rychle identifikovat.

Následující typy prostředků poskytují náhled vizuálního rozložení: rastrový obrázek, dialog, ikona, nabídka, kurzor, panel nástrojů

Následující zdroje neposkytují vizuální náhled: akcelerátor, manifest, tabulka řetězců, informace o verzi.

> [!NOTE]
> Pro náhled prostředků vyžaduje Win32.

### <a name="to-preview-resources"></a>Náhled prostředků

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources) nebo okně dokumentu vyberte prostředek, například **IDD_ABOUTBOX**.

1. V [okno Vlastnosti](/visualstudio/ide/reference/properties-window)vyberte tlačítko **stránky vlastností** .

   > [!TIP]
   > Použijte zástupce, přejděte do nabídky **zobrazení** > **stránky vlastností**.

   Otevře se stránka **vlastností** prostředku se zobrazením náhledu tohoto prostředku. Pomocí kláves se šipkami **nahoru** a **dolů** můžete procházet stromové ovládací prvky v **prostředky** nebo v okně dokumentu. Stránka **vlastností** zůstane otevřená a zobrazí všechny prostředky, které mají fokus a můžou se zobrazit v náhledu.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>
