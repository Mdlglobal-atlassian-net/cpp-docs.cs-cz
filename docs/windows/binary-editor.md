---
title: Binární Editor (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 420c5ecf44f8e8b264d9eafd93de58c0db3bedf4
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210715"
---
# <a name="binary-editor-c"></a>Binární Editor (C++)

> [!CAUTION]
> Úprava prostředků jako dialogová okna, obrázky nebo nabídky **binární Editor** je nebezpečné. Nesprávné úpravy mohou prostředek poškodit a učinit jej nečitelným v jeho nativním editoru.

**Binární Editor** umožňuje upravovat libovolný prostředek na binární úrovni v šestnáctkovém formátu nebo ve formátu ASCII. Můžete také použít [najít – příkaz](/visualstudio/ide/reference/find-command) k vyhledání řetězce ASCII nebo šestnáctkové bajty. Použití **binární Editor** pouze pokud potřebujete zobrazit nebo provést menší změny vlastní prostředky nebo typy prostředků nejsou podporovány prostředím Visual Studio.

Chcete-li otevřít **binární Editor** na nový soubor, přejděte do nabídky **souboru** > **nový** > **souboru**, vyberte typ soubor, kterou chcete upravit a pak vyberte rozevírací šipku vedle položky **otevřít** a tlačítko **otevřít v** > **binární Editor**.

Chcete-li otevřít **binární Editor** na existující soubor, přejděte do nabídky **souboru** > **otevřete** > **souboru**, vyberte soubor, kterou chcete upravit a pak vyberte rozevírací šipku vedle položky **otevřít** a tlačítko **otevřít v** > **binární Editor**.

   ![Binary Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Binární data pro dialogové okno se zobrazí v **binární Editor**

Jenom konkrétní hodnoty ASCII jsou reprezentovány v **binární Editor** (0x20 prostřednictvím 0x7E). Rozšířené znaky zobrazují jako tečky v pravém panelu ASCII hodnota části **binární Editor**. Tisknutelný znaky jsou hodnoty ASCII 32 prostřednictvím 126.

> [!TIP]
> Při použití **binární Editor**, v mnoha případech je můžete kliknout pravým tlačítkem na Zobrazit místní nabídku příkazů specifických pro prostředky. Dostupné příkazy závisí na položce, na kterou právě ukazuje kurzor. Například pokud klepnete na tlačítko při přejdete **binární Editor** se zvolenými šestnáctkovými hodnotami v místní nabídce se zobrazuje **Vyjmout**, **kopírování**, a **vložit**  příkazy.

**Binární Editor** není k dispozici ve verzích Express.

## <a name="how-to"></a>Postupy

**Binární Editor** vám umožní:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Chcete-li otevřít prostředek klasické pracovní plochy Windows pro binární úpravy

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte soubor konkrétní prostředek, který chcete upravit.

1. Klikněte pravým tlačítkem na zdroj a vyberte **Open binární Data**.

> [!NOTE]
> Pokud používáte [zobrazení prostředků](../windows/resource-view-window.md) okno otevřít prostředek ve formátu sady Visual Studio nerozpozná, jako je například RCDATA nebo vlastní prostředek, prostředek se automaticky otevře v **binární Editor**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Otevřete spravovaný prostředek pro binární úpravy

1. V **Průzkumníka řešení**, vyberte soubor konkrétní prostředek, který chcete upravit.

1. Klikněte pravým tlačítkem na zdroj a vyberte **otevřít v**.

1. V **otevřít v** dialogového okna zvolte **binární Editor**.

> [!NOTE]
> Můžete použít [Editor obrázků](../windows/image-editor-for-icons.md) a **binární Editor** pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

### <a name="to-edit-a-resource"></a>Chcete-li upravit prostředek

> [!NOTE]
> Pokud chcete použít **binární Editor** na prostředek již upravována v jiném okně editor, zavřete ostatní okna editoru nejprve.

1. Vyberte bajtů, které chcete upravit.

   **Kartu** klíč přesune fokus mezi šestnáctkové a části ASCII **binární Editor**. Můžete použít **Page Up** a **Page Down** klíče procházení jednu obrazovku prostředků najednou.

1. Zadejte novou hodnotu.

   Hodnota se změní okamžitě, v šestnáctkovém a části ASCII a se pozornost zaměří na nejbližší hodnotu v řádku.

> [!NOTE]
> **Binární Editor** přijímá změny automaticky při zavření editoru.

### <a name="to-find-binary-data"></a>Chcete-li vyhledat binární data

Můžete vyhledat řetězce ASCII nebo šestnáctkové bajty. Chcete-li například najít *Hello*, můžete vyhledat buď řetězec *Hello* nebo její šestnáctkové hodnoty *48 65 6C 6 6 C f*.

1. Z **upravit** nabídce zvolte [najít](/visualstudio/ide/reference/find-command).

1. V **najít** pole, vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte data, které chcete najít.

1. Vyberte některou z **najít** možnosti a vyberte **najít další**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Chcete-li vytvořit nový vlastní nebo datový prostředek

Můžete vytvořit nový vlastní nebo datový prostředek tak, že prostředek v samostatném souboru pomocí syntaxe souboru normální prostředku skriptů (.rc) a včetně souboru kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete  **Prostředek zahrnuje**.

1. [Vytvořte soubor .rc](../windows/how-to-create-a-resource-script-file.md) , který obsahuje vlastní nebo datový prostředek.

   Můžete zadat vlastní data v souboru .rc, jako v uvozovkách řetězec zakončený hodnotou null, nebo jako celá čísla ve formátu desítkové, hexadecimální nebo osmičkové soustavě.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor .rc váš projekt a vyberte **prostředek zahrnuje**.

1. V **směrnice času kompilace** zadejte `#include` příkaz, který poskytuje název souboru, který obsahuje vaše vlastní prostředek, třeba:

    ```cpp
    #include mydata.rc
    ```

   Ujistěte se, že syntaxe a pravopisu, co zadáte jsou správné. Obsah **směrnice času kompilace** pole jsou vloženy do souboru skriptu prostředků přesně tak, jak při zadávání.

1. Vyberte **OK** zaznamenat vaše změny.

Dalším způsobem, jak vytvořit vlastní prostředek se má importovat jako vlastní prostředek externího souboru, naleznete v tématu [jak: Správa prostředků](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Vytvoření nového vlastního prostředku nebo data prostředků vyžaduje Win32.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)