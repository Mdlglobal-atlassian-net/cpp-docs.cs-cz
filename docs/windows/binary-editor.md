---
title: Binární editor (C++)
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
ms.openlocfilehash: 591a6714f1adabb30fda446cad0e79e2c28c30ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215238"
---
# <a name="binary-editor-c"></a>Binární editor (C++)

> [!CAUTION]
> Úpravy prostředků, jako jsou dialogová okna, obrázky nebo nabídky v **binárním editoru** , jsou nebezpečné. Nesprávné úpravy mohou prostředek poškodit a učinit jej nečitelným v jeho nativním editoru.

**Binární editor** umožňuje upravovat libovolný prostředek na binární úrovni buď ve formátu hexadecimálního, nebo ve formátu ASCII. Můžete také použít [příkaz find](/visualstudio/ide/reference/find-command) a vyhledat buď řetězce ASCII, nebo hexadecimální bajty. **Binární editor** použijte pouze v případě, že potřebujete zobrazit nebo udělat drobné změny vlastních prostředků nebo typů prostředků, které nejsou podporovány prostředím Visual Studio. **Binární editor** není v edicích Express k dispozici.

- Chcete-li otevřít **binární editor** na novém souboru, přejděte do **souboru** nabídky > **novém** > **souboru**, vyberte typ souboru, který chcete upravit, poté vyberte rozevírací šipku vedle tlačítka **otevřít** a zvolte možnost **otevřít v** > **binárním editoru**.

- Chcete-li otevřít **binární editor** v existujícím souboru, přejděte do **souboru** nabídky > **otevřete** > **souboru**, vyberte soubor, který chcete upravit, poté vyberte rozevírací šipku vedle tlačítka **otevřít** a zvolte možnost **otevřít v** > **binárním editoru**.

   ![Binární editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Binární data dialogového okna zobrazeného v **binárním editoru**

V **binárním editoru** (0X20 prostřednictvím 0x7e) jsou reprezentovány pouze některé hodnoty ASCII. Rozšířené znaky se zobrazí jako tečky v sekci hodnota ASCII v pravém panelu **binárního editoru**. Tisknutelné znaky jsou hodnoty ASCII 32 až 126.

> [!TIP]
> Při použití **binárního editoru**můžete v mnoha případech kliknout pravým tlačítkem myši a zobrazit místní nabídku příkazů specifických pro prostředky. Dostupné příkazy závisí na položce, na kterou právě ukazuje kurzor. Pokud například kliknete pravým tlačítkem na **binární editor** se zvolenými hexadecimálními hodnotami, v místní nabídce se zobrazí příkazy **Vyjmout**, **Kopírovat**a **Vložit** .

## <a name="how-to"></a>Postup

**Binární editor** vám umožní:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Otevření prostředku stolního počítače s Windows pro binární úpravy

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)vyberte konkrétní soubor prostředků, který chcete upravit.

1. Klikněte pravým tlačítkem na prostředek a vyberte **Otevřít binární data**.

> [!NOTE]
> Použijete-li okno **prostředky** k otevření prostředku s formátem, který aplikace Visual Studio nerozpozná, jako je například RCDATA nebo vlastní prostředek, je prostředek automaticky otevřen v **binárním editoru**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Otevření spravovaného prostředku pro binární úpravy

1. V **Průzkumník řešení**vyberte konkrétní soubor prostředků, který chcete upravit.

1. Klikněte pravým tlačítkem na prostředek a vyberte **otevřít v**.

1. V dialogovém okně **otevřít** v vyberte možnost **binární editor**.

> [!NOTE]
> Můžete použít [Editor obrázků](../windows/image-editor-for-icons.md) a **binární editor** pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

### <a name="to-edit-a-resource"></a>Úprava prostředku

Chcete-li použít **binární editor** u prostředku, který je již upravován v jiném okně editoru, nejprve zavřete okno editoru.

1. Vyberte bajt, který chcete upravit.

   Klávesa **TAB** přesouvá fokus mezi oddíly hexadecimálního a ASCII v **binárním editoru**. Pomocí kláves **Page Up** a **Page Down** můžete procházet prostředky po jednotlivých obrazovkách.

1. Zadejte novou hodnotu.

   Hodnota se okamžitě změní v sekcích hexadecimálního i ASCII a fokus se přesune na další hodnotu v řádku.

> [!NOTE]
> **Binární editor** přijímá změny automaticky při zavření editoru.

### <a name="to-find-binary-data"></a>Hledání binárních dat

Můžete hledat buď řetězce ASCII, nebo hexadecimální bajty. Chcete-li například najít *Hello*, můžete vyhledat řetězec *Hello* nebo jeho hexadecimální hodnotu, *48 65 6c 6c 6F*.

1. Přejděte do nabídky **upravit** > [Najít](/visualstudio/ide/reference/find-command).

1. V poli **Najít** vyberte předchozí hledaný řetězec z rozevíracího seznamu nebo zadejte data, která chcete najít.

1. Vyberte některou z možností **hledání** a zvolte **Najít další**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Vytvoření nového vlastního prostředku nebo zdroje dat

Nový vlastní nebo datový prostředek můžete vytvořit tak, že ho umístíte do samostatného souboru pomocí syntaxe normálního souboru skriptu prostředků (. RC) a pak tento soubor zadáte tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **prostředek**včetně.

1. [Vytvořte soubor. RC](../windows/how-to-create-a-resource-script-file.md) , který obsahuje vlastní nebo datový prostředek.

   Vlastní data můžete zadat v souboru. RC jako řetězce v uvozovkách zakončené hodnotou null nebo jako celá čísla v desítkovém, šestnáctkovém nebo osmičkovém formátu.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor. RC projektu a vyberte možnost **prostředek zahrnuje**.

1. Do pole **direktivy pro kompilaci** zadejte příkaz `#include`, který poskytuje název souboru obsahujícího vlastní prostředek, například:

    ```cpp
    #include mydata.rc
    ```

   Ujistěte se, že syntaxe a pravopis, co zadáte, jsou správné. Obsah pole direktiv v **době kompilace** je vložen do souboru skriptu prostředků přesně tak, jak je zadáte.

1. Vyberte **OK** a zaznamenejte změny.

Dalším způsobem, jak vytvořit vlastní prostředek, je importovat externí soubor jako vlastní prostředek, viz [How to: Manage Resources](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Vytváření nových vlastních nebo datových zdrojů vyžaduje Win32.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)
