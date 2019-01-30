---
title: Binární Editor (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 06c4a224b745f5aba8c9105d32489f8ca3109e1c
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293595"
---
# <a name="binary-editor-c"></a>Binární Editor (C++)

> [!WARNING]
> **Binární Editor** není k dispozici ve verzích Express.

Binární editor umožňuje upravovat libovolný prostředek na binární úrovni v šestnáctkovém formátu nebo ve formátu ASCII. Můžete také použít [najít – příkaz](/visualstudio/ide/reference/find-command) k vyhledání řetězce ASCII nebo šestnáctkové bajty. Měli byste použít **binární** editor jenom v případě, že potřebujete zobrazit nebo provést menší změny vlastní prostředky nebo typy prostředků nejsou podporovány prostředím Visual Studio.

Otevřete **binární Editor**, zvolte nejprve **souboru** > **nový** > **souboru** v hlavní nabídce vyberte soubor, kterou chcete upravit a potom klikněte na rozevírací šipku vedle položky **otevřít** a tlačítko **otevřít v** > **binární Editor**.

> [!CAUTION]
> Úprava prostředků jako dialogová okna, obrázky nebo nabídky pomocí binárního editoru není bezpečná. Nesprávné úpravy mohou prostředek poškodit a učinit jej nečitelným v jeho nativním editoru.

> [!TIP]
> Při použití **binární** editoru v mnoha případech je můžete kliknout pravým tlačítkem na Zobrazit místní nabídku příkazů specifických pro prostředky. Dostupné příkazy závisí na položce, na kterou právě ukazuje kurzor. Například pokud klepnete na tlačítko při přejdete **binární** editor se zvolenými šestnáctkovými hodnotami, v místní nabídce se zobrazuje **Vyjmout**, **kopírování**, a **vložit**  příkazy.

## <a name="binary-editor-how-to"></a>Postupy binární Editor

S **binární** editoru, najdete v následujících akcí:

### <a name="to-open-a-resource-for-binary-editing"></a>Chcete-li otevřít prostředek pro binární úpravy

#### <a name="to-open-a-windows-desktop-resource"></a>Chcete-li otevřít prostředek klasické pracovní plochy Windows

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte soubor konkrétní prostředek, který chcete upravit.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. Klikněte pravým tlačítkem na zdroj a klikněte na tlačítko **Open binární Data** z místní nabídky.

   > [!NOTE]
   > Pokud používáte [zobrazení prostředků](../windows/resource-view-window.md) okno otevřít prostředek ve formátu, že Visual Studio nedokáže rozpoznat (například RCDATA nebo vlastní prostředek), prostředek se automaticky otevře v **binární** editoru.

#### <a name="to-open-a-managed-resource"></a>Otevřete spravovaný prostředek

1. V **Průzkumníka řešení**, vyberte soubor konkrétní prostředek, který chcete upravit.

1. Klikněte pravým tlačítkem na prostředek a zvolte **otevřít v** z místní nabídky.

1. V **otevřít v** dialogového okna zvolte **binární Editor**.

   > [!NOTE]
   > Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

![Binary Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
Binární Data pro dialogové okno se zobrazí v binárním editoru

Jenom konkrétní hodnoty ASCII jsou reprezentovány v binárním editoru (0x20 prostřednictvím 0x7E). Rozšířené znaky zobrazují jako tečky v části hodnotu ASCII binární editor (pravý panel). "Tisknutelné" znaky jsou hodnoty ASCII 32 prostřednictvím 126.

> [!NOTE]
> Pokud chcete použít **binární** editor prostředku už upravována v jiném okně editoru nejprve zavřít ostatní okna editoru.

### <a name="to-edit-a-resource-in-the-binary-editor"></a>Úprava prostředků v binárním editoru

1. Vyberte bajtů, které chcete upravit.

   **Kartu** klíč přesune fokus mezi šestnáctkové a části ASCII **binární** editoru. Můžete použít **Page Up** a **Page Down** klíče procházení jednu obrazovku prostředků najednou.

1. Zadejte novou hodnotu.

   Hodnota se změní okamžitě, v šestnáctkovém a části ASCII a se pozornost zaměří na nejbližší hodnotu v řádku.

   > [!NOTE]
   > **Binární** editor přijímá změny automaticky při zavření editoru.

### <a name="to-find-binary-data"></a>Chcete-li vyhledat binární data

Můžete vyhledat řetězce ASCII nebo šestnáctkové bajty. Například pokud chcete vyhledat "Hello", můžete vyhledat buď řetězec "Hello", nebo pro "48 65 6C 6 6 C f" (v šestnáctkové soustavě ekvivalent).

1. Z **upravit** nabídce zvolte [najít](/visualstudio/ide/reference/find-command).

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte data, které chcete najít.

1. Vyberte některou z **najít** možnosti.

1. Vyberte **najít další**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Chcete-li vytvořit nový vlastní nebo datový prostředek

Můžete vytvořit nový vlastní nebo datový prostředek tak, že prostředek v samostatném souboru pomocí syntaxe souboru normální prostředku skriptů (.rc) a včetně souboru kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a kliknete na  **Prostředek zahrnuje** v místní nabídce.

1. [Vytvořte soubor .rc](../windows/how-to-create-a-resource-script-file.md) , který obsahuje vlastní nebo datový prostředek.

   Můžete zadat vlastní data v souboru .rc, jako v uvozovkách řetězec zakončený hodnotou null, nebo jako celá čísla ve formátu desítkové, hexadecimální nebo osmičkové soustavě.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na souboru .rc v projektu a pak klikněte na tlačítko **prostředek zahrnuje** v místní nabídce.

1. V **směrnice času kompilace** zadejte `#include` příkaz, který poskytuje název souboru, který obsahuje vaše vlastní prostředek. Příklad:

    ```cpp
    #include mydata.rc
    ```

   Ujistěte se, že syntaxe a pravopisu, co zadáte jsou správné. Obsah **směrnice času kompilace** pole jsou vloženy do souboru skriptu prostředků přesně tak, jak jste je zadali.

1. Vyberte **OK** zaznamenat vaše změny.

Dalším způsobem, jak vytvořit vlastní prostředek se má importovat jako vlastní prostředek externího souboru. Další informace najdete v tématu [import a export prostředků](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Vytvoření nového vlastního prostředku nebo data prostředků vyžaduje Win32.

## <a name="managed-resources"></a>Spravované prostředky

Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a **binární** editor pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)