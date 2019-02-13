---
title: Editory prostředků (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 43eab011cefed116723bd983b685c1c8c230326f
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226316"
---
# <a name="resource-editors-c"></a>Editory prostředků (C++)

A **prostředků** editoru je specializované prostředí pro vytváření nebo úprav prostředky, které jsou součástí projektu sady Visual Studio. Editory prostředků Visual Studio techniky a rozhraní vám pomůžou vytvářet a upravovat prostředky aplikace rychle a snadno sdílet. Editory prostředků umožňují zobrazit a upravit prostředky v příslušné prostředky editoru a ve verzi preview.

Otevře se editor odpovídající automaticky při vytvoření nebo otevření prostředku.

> [!NOTE]
> Protože spravované projekty nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

|Použití...|Chcete-li upravit...|
|----------------|----------------|
|[Editor akcelerátorů](../windows/accelerator-editor.md)|Tabulek akcelerátorů v projektech Visual C++.|
|[Binární editor](binary-editor.md)|Informace o binárních dat a vlastních prostředků v projektech Visual C++, Visual Basic nebo Visual C#.|
|[Editor dialogových oken](../windows/dialog-editor.md)|Dialogová okna v projektech Visual C++.|
|[Editor obrázků](../windows/image-editor-for-icons.md)|Rastrové obrázky, ikony, kurzory a další soubory obrázků v projektech Visual C++, Visual Basic nebo Visual C#.|
|[Editor nabídek](../windows/menu-editor.md)|Prostředky nabídky v projektech Visual C++.|
|[Ribbon Editor](../mfc/ribbon-designer-mfc.md)|Prostředky z pásu karet v projektech knihovny MFC.|
|[Editor řetězce](../windows/string-editor.md)|Řetězec tabulek v projektech Visual C++.|
|[Editor panelu nástrojů](../windows/toolbar-editor.md)|Prostředky panelu nástrojů v projektech Visual C++. Editor panelu nástrojů je součástí editoru obrázků.|
|[Editor informací o verzi](../windows/version-information-editor.md)|Informace o verzi v projektech Visual C++.|

## <a name="view-and-edit-resources-in-a-resource-editor"></a>Zobrazení a úprava prostředků v editoru prostředků

Každý typ prostředku má **prostředků** editor specifické pro příslušný typ prostředku. Můžete změnit uspořádání, změňte velikost, přidat ovládací prvky a funkce nebo jinak upravit aspektů prostředku pomocí editoru přidružené. Můžete také upravit prostředek v [textový formát](../windows/how-to-open-a-resource-script-file-in-text-format.md) a [binární formát](../windows/opening-a-resource-for-binary-editing.md).

Některé typy prostředků jsou jednotlivé soubory, které můžete importovat a používat různými způsoby; patří mezi ně rastrové obrázky, ikony, kurzory, panely nástrojů a soubory html. Tyto zdroje mají názvy souborů a [identifikátory prostředků](../windows/symbols-resource-identifiers.md). Jiné, jako je například dialogová okna, nabídek a tabulky řetězců v projekty Win32, existují pouze v rámci prostředku skriptů (.rc) souboru nebo souboru prostředků (.rct) šablony.

Prostředky můžete také upravit mimo projekt, naleznete v tématu [jak: Otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Vlastnosti prostředku [lze upravit pomocí okna vlastnosti](../windows/changing-the-properties-of-a-resource.md).

Chcete-li upravit vlastnosti prostředku:

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na prostředku, kterou chcete upravit a zvolte **vlastnosti** z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), změna vlastností prostředku.

Vrátit zpět změny provedené na vlastnosti prostředku:

1. Ujistěte se, že váš prostředek má fokus **zobrazení prostředků**.

1. Zvolte **zpět** z **upravit** nabídky.

### <a name="win32-resources"></a>Prostředky Win32

Budete mít přístup k prostředkům Win32 v [zobrazení prostředků](../windows/resource-view-window.md) podokně.

Chcete-li zobrazit prostředek systému Win32 v editoru prostředků:

1. Vyberte **zobrazení prostředků** z **zobrazení** nabídky.

1. Pokud **zobrazení prostředků** okno nejsou nejvrchnější okna, vyberte **zobrazení prostředků** kartu a přenést ho do horní části.

1. Z **zobrazení prostředků**, rozbalte složku pro projekt, který obsahuje prostředky, které chcete zobrazit. Například pokud chcete zobrazit prostředku dialogového okna, rozbalte **dialogové okno** složky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. Dvakrát klikněte na prostředek, třeba **IDD_ABOUTBOX**.

   Prostředek se otevře ve vhodném editoru. Například pro prostředky dialogového okna, prostředek se otevře uvnitř **dialogové okno** editoru.

   Můžete také [zobrazit prostředky v souboru .rc (skript prostředků) bez nutnosti otevřít projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

Pokud chcete odstranit existující prostředek Win 32:

1. V **zobrazení prostředků**, rozbalte uzel pro typ prostředku.

2. Klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit** z místní nabídky.

   > [!NOTE]
   > Můžete odstranit prostředků pomocí příkazu stejné místní nabídky v případě, že máte soubor .rc otevřený v okna dokumentu mimo projekt.

### <a name="resources-in-managed-projects"></a>Prostředky ve spravovaných projektech

Protože spravovaných projektů nepoužívejte soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Chcete-li zobrazit spravovaných prostředků v editoru prostředků:

V **Průzkumníka řešení**, dvakrát klikněte na prostředek, třeba *Bitmap1.bmp*.

   Prostředek se otevře ve vhodném editoru.

Pokud chcete odstranit existující spravovaný prostředek:

V **Průzkumníka řešení**, klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit** z místní nabídky.

## <a name="preview-resources"></a>Náhled prostředků

Ve verzi Preview vašich prostředků, aby bylo možné zobrazit grafických prostředků bez jejich otevírání. V předběžné verzi je také užitečné pro spustitelné soubory, poté, co jste je zkompilovat, protože identifikátory prostředků změnit na čísla. Protože tyto identifikátory číselné často neposkytuje dostatek informací, zobrazení náhledu prostředky vám pomůže rychle identifikovat.

Rozložení vizuálu z těchto typů prostředků můžete zobrazit náhled: Rastrový obrázek, dialogové okno, ikona, nabídka, kurzor, panel nástrojů

Funkce visual ve verzi preview se nevztahuje na prostředky: Akcelerátor, Manifest, tabulka řetězců a informace o verzi

> [!NOTE]
> Náhled prostředků vyžaduje Win32.

Náhled zdroje:

1. V [zobrazení prostředků](../windows/resource-view-window.md) nebo okno dokumentu, vyberte prostředek, třeba `IDD_ABOUTBOX`.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), vyberte **stránky vlastností** tlačítko.

   > [!TIP]
   > Pro místní v **zobrazení** nabídce vyberte možnost **stránky vlastností**.

   **Stránku vlastností** prostředek se otevře zobrazení ve verzi preview tohoto prostředku. Pak můžete použít **nahoru** a **dolů** v ovládacím prvku klávesy se šipkami přejdete strom **zobrazení prostředků** nebo okno dokumentu. **Stránku vlastností** zůstávají otevřené, který se zobrazí jakémukoli prostředku, který má právě fokus a můžete zobrazit jejich náhled.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)