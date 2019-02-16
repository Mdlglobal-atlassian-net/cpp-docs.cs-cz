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
ms.openlocfilehash: 1f176b3fa19374b402039ecca60e690ade5c0cef
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320624"
---
# <a name="how-to-manage-resources-c"></a>Postupy: Správa prostředků (C++)

## <a name="copy-resources"></a>Kopírování prostředků

Prostředky můžete zkopírovat z jednoho souboru do jiného beze změny nebo může změna jazyka nebo podmínky prostředku během kopírování ji.

Prostředky můžete snadno zkopírovat z existující prostředek nebo spustitelného souboru k aktuálnímu souboru prostředků. Se zkopírovat prostředky, které otevřete oba soubory, které obsahují prostředky ve stejnou dobu a přetáhněte položky z jednoho souboru do jiného nebo kopírování a vkládání mezi dva soubory. Tato metoda se dá použít pro soubory skriptů (.rc) prostředků a soubory prostředků šablon (.rct) a jako spustitelné soubory (.exe).

> [!NOTE]
> Visual C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své aplikaci. Další informace najdete v tématu [Klipart: Běžným prostředkům](https://github.com/Microsoft/VCSamples).

Můžete použít metodu a přetažení mezi soubory .rc, které jsou otevřené [mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Kopírování prostředků mezi soubory pomocí přetahování myší – metoda

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazit prostředky v souboru .rc mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například otevřete *Source1.rc* a *Source2.rc*.

1. V prvním .rc souboru vyberte zdroj, který chcete kopírovat. Například v *Source1.rc*vyberte **IDD_DIALOG1**.

1. Podržte stisknutou klávesu **Ctrl** klíče a přetáhněte prostředek do druhého souboru .rc. Například, přetáhněte **IDD_DIALOG1** z *Source1.rc* k *Source2.rc*.

   > [!NOTE]
   > Přetažení prostředku bez podržení **Ctrl** klíč přesunu prostředku místo jeho kopírování.

### <a name="to-copy-resources-using-copy-and-paste"></a>Kopírování prostředků pomocí kopírování a vložení

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazit prostředky v souboru .rc mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například *Source1.rc* a *Source2.rc*.

1. Ve zdrojovém souboru, ze kterého chcete kopírovat prostředek (například *Source1.rc*), klikněte pravým tlačítkem na prostředek a zvolte **kopírování** z místní nabídky.

1. Klikněte pravým tlačítkem na soubor prostředků, do které chcete vložit prostředku (například *Source2.rc*). Zvolte **vložit** z místní nabídky.

   > [!NOTE]
   > Nelze přetáhnout a vyřadit, kopírování, vyjmutí nebo vložte mezi soubory prostředků v projektu (**zobrazení prostředků**) a samostatné .rc soubory (ty otevřít v systému windows dokumentu). Můžete to udělat v předchozích verzích produktu.

   > [!NOTE]
   > Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor, Visual C++ změnit hodnotu symbolu přenesené prostředků nebo název symbolu a hodnota při kopírování do nového souboru.

### <a name="change-the-language-or-condition-of-a-resource-while-copying"></a>Změna jazyka nebo podmínky prostředku během kopírování

Při kopírování v prostředku, můžete změnit jeho vlastnost jazyka vlastnost podmínka nebo obojí.

- Určuje jazyk prostředku přesně to, jazyk prostředku. Jazyk používá [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) vám pomůže identifikovat prostředek, pro který potřebujete. (Ale prostředky mohou mít rozdíly pro jednotlivé jazyky, které se vztahují na text, například akcelerátory, které může fungovat jenom na použití japonské klávesnice nebo rastrový obrázek, který může být pouze vhodné pro čínštinu lokalizované sestavení.)

- Podmínky prostředku je definovaný symbol, který určuje podmínku, pod kterým se má použít tento konkrétní kopie prostředku.

Jazyk a podmínky prostředku jsou uvedeny v závorkách za názvem prostředku v **pracovní prostor** okna. V tomto příkladu s názvem prostředku `IDD_AboutBox` používá `Finnish` jako svůj jazyk a jeho stav je `XX33`.

```cpp
IDD_AboutBox (Finnish - XX33)
```

#### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Kopírovat existující prostředek a změnit jeho jazyka nebo podmínky

1. V souboru .rc nebo v [zobrazení prostředků](../windows/resource-view-window.md) okna, klikněte pravým tlačítkem na prostředek, které chcete kopírovat.

1. Zvolte **vložit kopii** z místní nabídky a nastavte následující:

   - Pro **jazyk** seznamu, vyberte jazyk.

   - V **podmínku** zadejte podmínku.

## <a name="edit-resources"></a>Upravit prostředky

Soubory spravovaného prostředku (RESX) jsou soubory formátu XML. Když přidáte spravovaný soubor prostředků do projektu z **přidat novou položku** dialogovém okně **editoru spravovaných prostředků** otevře ve výchozím nastavení.

## <a name="import-and-export-resources"></a>Import a Export prostředků

Můžete importovat grafických prostředků (rastrové obrázky, ikony, kurzory a panely nástrojů), soubory HTML a vlastní prostředky pro použití v jazyce Visual C++. Stejné typy souborů, můžete exportovat z projektu Visual C++ do samostatných souborů, které lze použít mimo vývojové prostředí.

> [!NOTE]
> Typy prostředků jako akcelerátory, dialogová okna a tabulky řetězců nelze importovaná nebo exportovaná, protože nejsou typy samostatný soubor.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Importovat jednotlivé prostředky do aktuálního souboru prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na uzel pro skript prostředků (* .rc) soubor, ke kterému chcete přidat prostředek.

1. Vyberte **Import** v místní nabídce.

1. Vyhledejte a vyberte název souboru rastrový obrázek (BMP), ikona (), kurzor (), soubor Html (.htm) nebo jiný soubor, který chcete importovat.

1. Zvolte **OK** bude příslušný materiál přidán na vybraný soubor v **prostředků** zobrazení.

   > [!NOTE]
   > Proces importu funguje stejným způsobem bez ohledu na to, který prostředek se konkrétní typ jste vybrali. Importovaných zdrojů je automaticky přidán do správný uzel pro příslušný typ prostředku.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Chcete-li exportovat bitmapy, ikony nebo kurzoru jako samostatný soubor (pro použití mimo aplikaci Visual C++)

1. V **prostředků** zobrazení, klikněte pravým tlačítkem na prostředku, kterou chcete exportovat.

1. Vyberte **exportovat** v místní nabídce a následně přijímal aktuální název souboru nebo zadejte nový.

1. Přejděte do složky, kam chcete uložit soubor a zvolte **exportovat**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md)<br/>
[Zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md)<br/>