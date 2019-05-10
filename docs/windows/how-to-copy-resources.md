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
ms.openlocfilehash: 28678b560387fa6b111d60a7487ed44f9244a821
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449058"
---
# <a name="how-to-manage-resources-c"></a>Postupy: Správa prostředků (C++)

## <a name="copy-and-edit-resources"></a>Kopírovat a upravit prostředky

Prostředky můžete zkopírovat z jednoho souboru do druhého bez jejich změny nebo změna jazyka nebo podmínky prostředku během kopírování.

Prostředky můžete snadno zkopírovat z existující prostředek nebo spustitelného souboru k aktuálnímu souboru prostředků. Se zkopírovat prostředky, které otevřete oba soubory, které obsahují prostředky ve stejnou dobu a přetáhněte položky z jednoho souboru do jiného nebo kopírování a vkládání mezi dva soubory. Tato metoda se dá použít pro soubory skriptů (.rc) prostředků a soubory prostředků šablon (.rct) a jako spustitelné soubory (.exe).

> [!NOTE]
> Visual C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své aplikaci. Další informace najdete v tématu [Klipart: Běžným prostředkům](https://github.com/Microsoft/VCSamples).

Nelze přetáhnout a vyřadit, kopírování, vyjmutí nebo vložte mezi soubory prostředků v projektu (**zobrazení prostředků**) a otevírání souborů .rc samostatné v dokumentu systému windows. Můžete to udělat v předchozích verzích produktu. Pouze pomocí metody a přetažení mezi soubory .rc, které jsou otevřeny mimo projekt.

### <a name="to-copy-resources"></a>Chcete-li kopírovat zdroje

1. Otevřete oba samostatné soubory prostředků. (Viz [použijte soubory skriptu prostředků](how-to-create-a-resource-script-file.md#use-resource-script-files)). Například otevřete *Source1.rc* a *Source2.rc*.

1. V prvním .rc souboru, buď:

   - Pomocí této metody přetažení myší

      1. Vyberte prostředek, který chcete kopírovat. Například v *Source1.rc*vyberte **IDD_DIALOG1**.

      1. Podržte stisknutou klávesu **Ctrl** klíče a přetáhněte prostředek do druhého souboru .rc. Například, přetáhněte **IDD_DIALOG1** z *Source1.rc* k *Source2.rc*.

         > [!TIP]
         > Přetažení prostředku bez podržení **Ctrl** klíč přesunu prostředku místo jeho kopírování.

   - Použít zkopírování a vložení – metoda

      1. Klikněte pravým tlačítkem na zdroj vám ke kopírování (například *Source1.rc*) a zvolte **kopírování**.

      1. Klikněte pravým tlačítkem na soubor prostředků, do které chcete vložit prostředku (například *Source2.rc*) a zvolte **vložte**.

> [!NOTE]
> Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor, Visual C++ změnit hodnotu symbolu přenesené prostředků nebo název symbolu a hodnota při kopírování do nového souboru.

Při kopírování v prostředku, můžete změnit jeho vlastnost jazyka vlastnost podmínka nebo obojí.

- Jazyk prostředku, který určuje jazyk, který používá [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) vám pomůže identifikovat prostředek, pro který potřebujete. Prostředky mohou mít rozdíly pro jednotlivé jazyky, které se vztahují na text, například akcelerátory, které může fungovat jenom na použití japonské klávesnice nebo rastrový obrázek, který může být pouze vhodné pro čínštinu lokalizované sestavení.

- Podmínky prostředku je definovaný symbol, který určuje podmínku, pod kterým se má použít tento konkrétní kopie prostředku.

Jazyk a podmínky prostředku jsou uvedeny v závorkách za názvem prostředku v **pracovní prostor** okna. V tomto poli s názvem prostředku `IDD_AboutBox` používá `Finnish` jako svůj jazyk a jeho stav je `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Kopírovat existující prostředek a změnit jeho jazyka nebo podmínky

V *.rc* souboru nebo [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources) okna, klikněte pravým tlačítkem na požadovaný prostředek zkopírovat a zvolte **vložit kopii**. Potom nastavte následující:

- Pro **jazyk** seznamu, vyberte jazyk.

- V **podmínku** zadejte podmínku.

### <a name="to-edit-resources"></a>Chcete-li upravit prostředky

Spravované prostředky (RESX) soubory jsou soubory formátu XML. Když přidáte spravovaný soubor prostředků do projektu z **přidat novou položku** dialogovém okně **editoru spravovaných prostředků** otevře ve výchozím nastavení.

## <a name="import-and-export-resources"></a>Import a Export prostředků

Můžete importovat grafických prostředků (rastrové obrázky, ikony, kurzory a panely nástrojů), soubory HTML a vlastní prostředky pro použití v jazyce Visual C++. Stejné typy souborů, můžete exportovat ze sady Visual Studio C++ projektu do samostatných souborů, které lze použít mimo vývojové prostředí.

> [!NOTE]
> Typy prostředků jako akcelerátory, dialogová okna a tabulky řetězců nelze importovat nebo exportovat, protože nejsou typy samostatný soubor.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Pro import prostředku do souboru skriptu prostředků

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources) klikněte pravým tlačítkem na uzel skriptů (.rc) soubor prostředků, ke kterému chcete přidat prostředek a vyberte **Import**.

1. Vyhledejte a vyberte název souboru rastrového obrázku (BMP), ikony (ICO), kurzoru (.cur), soubor ve formátu html (.htm) nebo jiný soubor k importu.

1. Vyberte **OK** bude příslušný materiál přidán do souboru skriptu prostředků.

> [!NOTE]
> Proces importu funguje stejně bez ohledu na to, který prostředek zadejte, které jste vybrali. Importovaných zdrojů je automaticky přidán do správného uzlu daného typu prostředků.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Chcete-li exportovat prostředek pro použití mimo aplikaci Visual C++

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na požadovaný prostředek k exportu a vyberte **exportovat**. Můžete přijmout aktuální název souboru nebo zadejte nový.

1. Přejděte do složky, kam chcete uložit soubor a vyberte **exportovat**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: Vytvořit prostředky](../windows/how-to-create-a-resource-script-file.md)<br/>
[Postupy: Zahrnutí prostředků v čase kompilace](../windows/how-to-include-resources-at-compile-time.md)<br/>