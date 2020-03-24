---
title: 'Postupy: Správa prostředků (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 0af4e8faeb3d8606fb351b193364a2748fbc944e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215210"
---
# <a name="how-to-manage-resources-c"></a>Postupy: Správa prostředků (C++)

## <a name="copy-and-edit-resources"></a>Kopírování a úpravy prostředků

Můžete kopírovat prostředky z jednoho souboru do druhého, aniž byste je změnili, nebo změnit jazyk nebo podmínku prostředku při jeho kopírování.

Do aktuálního souboru prostředků můžete snadno kopírovat prostředky z existujícího prostředku nebo spustitelného souboru. Pokud chcete kopírovat prostředky, otevřete oba soubory, které obsahují prostředky, a přetáhněte položky z jednoho souboru na jiný nebo je zkopírujte a vložte mezi tyto dva soubory. Tato metoda se používá pro soubory skriptu prostředků (. RC) a soubory šablony prostředků (. RCT) a jako spustitelné soubory (. exe).

> [!NOTE]
> Vizuál C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své vlastní aplikaci. Další informace najdete v tématu věnovaném [klipartům: běžné prostředky](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general).

Nemůžete přetahovat, kopírovat, vyjmout ani vkládat soubory prostředků v projektu (**prostředky**) a samostatné soubory. RC otevřené v dokumentu okna. To můžete provést v předchozích verzích produktu. Použijte pouze metodu přetažení mezi soubory. RC, které jsou otevřeny mimo projekt.

### <a name="to-copy-resources"></a>Kopírování prostředků

1. Otevřete oba soubory prostředků samostatně. (Viz [použití souborů skriptu prostředků](how-to-create-a-resource-script-file.md#use-resource-script-files)). Otevřete například *source1. RC* a *SOURCE2. RC*.

1. Uvnitř prvního souboru. RC buď:

   - Použití metody přetažení

      1. Vyberte prostředek, který chcete zkopírovat. Například v *source1. RC*vyberte **IDD_DIALOG1**.

      1. Podržte stisknutou klávesu **CTRL** a přetáhněte prostředek k druhému souboru. rc. Přetáhněte například **IDD_DIALOG1** z *source1. RC* do *SOURCE2. RC*.

         > [!TIP]
         > Při přetahování prostředku bez podržení klávesy **CTRL** se místo kopírování bude prostředek přesouvat.

   - Použití metody kopírování a vložení

      1. Klikněte pravým tlačítkem na prostředek, který chcete zkopírovat (například *source1. RC*) a vyberte **Kopírovat**.

      1. Klikněte pravým tlačítkem na soubor prostředků, do kterého chcete prostředek vložit (například *SOURCE2. RC*), a vyberte **Vložit**.

> [!NOTE]
> Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnotami v existujícím C++ souboru, může vizuál při kopírování do nového souboru změnit hodnotu symbolu převedeného prostředku nebo název a hodnotu symbolu.

Při kopírování v prostředku můžete změnit jeho vlastnost jazyka nebo podmínky nebo obojí.

- Jazyk prostředku určuje jazyk používaný službou [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) , který vám usnadní identifikaci prostředku, pro který hledáte. Prostředky můžou mít rozdíly pro každý jazyk, který nesouvisí s textem, například akcelerátory, které můžou fungovat jenom na japonské klávesnici nebo na rastrovém obrázku, který by měl být vhodný jenom pro Čínskě lokalizovaná sestavení.

- Podmínka prostředku je definovaný symbol, který určuje podmínku, za kterou se má použít tato konkrétní kopie prostředku.

Jazyk a podmínka prostředku jsou uvedeny v závorkách za názvem prostředku v okně **pracovního prostoru** . Zde prostředek s názvem `IDD_AboutBox` používá `Finnish` jako svůj jazyk a jeho stav je `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Zkopírování existujícího prostředku a změna jeho jazyka nebo podmínky

V souboru *. RC* nebo v okně [prostředky](how-to-create-a-resource-script-file.md#create-resources) klikněte pravým tlačítkem na prostředek, který chcete zkopírovat a vyberte možnost **Vložit kopii**. Pak nastavte následující:

- V rozevíracím seznamu **jazyk** vyberte jazyk.

- Do pole **Podmínka** zadejte podmínku.

### <a name="to-edit-resources"></a>Úprava prostředků

Spravované soubory prostředků (. resx) jsou soubory XML. Když do projektu přidáte soubor spravovaného prostředku z dialogového okna **Přidat novou položku** , otevře se ve výchozím nastavení **Editor spravovaných prostředků** .

## <a name="import-and-export-resources"></a>Import a export prostředků

Můžete importovat grafické prostředky (rastrové obrázky, ikony, kurzory a panely nástrojů), soubory HTML a vlastní prostředky pro použití v jazyce Visual C++. Můžete exportovat stejné typy souborů z projektu sady Visual Studio C++ a oddělit soubory, které lze použít mimo vývojové prostředí.

> [!NOTE]
> Typy prostředků, jako jsou akcelerátory, dialogová okna a tabulky řetězců, se nedají importovat ani exportovat, protože nejsou samostatné typy souborů.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Import prostředku do souboru skriptu prostředků

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources) klikněte pravým tlačítkem myši na uzel souboru skriptu prostředků (. RC), do kterého chcete přidat prostředek, a vyberte **importovat**.

1. Vyhledejte a vyberte název souboru rastrového obrázku (. bmp), ikony (. ico), kurzor (. měna), soubor HTML (. htm) nebo jiný soubor k importu.

1. Vyberte **OK** a přidejte prostředek do souboru skriptu prostředků.

> [!NOTE]
> Proces importu funguje stejně bez ohledu na to, který typ prostředku jste vybrali. Importovaný prostředek se automaticky přidá do správného uzlu daného typu prostředku.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Export prostředku pro použití mimo vizuálC++

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem na prostředek, který chcete exportovat, a vyberte **exportovat**. Můžete přijmout aktuální název souboru nebo zadat nový.

1. Přejděte do složky, kam chcete soubor uložit, a vyberte **exportovat**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: vytváření prostředků](../windows/how-to-create-a-resource-script-file.md)<br/>
[Postupy: Zahrnutí prostředků v čase kompilace](../windows/how-to-include-resources-at-compile-time.md)
