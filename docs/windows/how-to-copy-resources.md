---
title: 'Postupy: Kopírování prostředků (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 772c9b905d4cb0c4e2ccab9ec51aa02860b2db32
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849658"
---
# <a name="how-to-copy-resources-c"></a>Postupy: Kopírování prostředků (C++)

Prostředky můžete zkopírovat z jednoho souboru do jiného beze změny nebo může změna jazyka nebo podmínky prostředku během kopírování ji.

Prostředky můžete snadno zkopírovat z existující prostředek nebo spustitelného souboru k aktuálnímu souboru prostředků. Se zkopírovat prostředky, které otevřete oba soubory, které obsahují prostředky ve stejnou dobu a přetáhněte položky z jednoho souboru do jiného nebo kopírování a vkládání mezi dva soubory. Tato metoda se dá použít pro soubory skriptů (.rc) prostředků a soubory prostředků šablon (.rct) a jako spustitelné soubory (.exe).

> [!NOTE]
> Visual C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své aplikaci. Další informace najdete v tématu [Klipart: Běžným prostředkům](https://github.com/Microsoft/VCSamples).

Můžete použít metodu a přetažení mezi soubory .rc, které jsou otevřené [mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

## <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Kopírování prostředků mezi soubory pomocí přetahování myší – metoda

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků, ve který #zahrnuje konce souboru mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například otevřete Source1.rc a Source2.rc.

1. V prvním .rc souboru vyberte zdroj, který chcete kopírovat. Například v `Source1.rc`vyberte **IDD_DIALOG1**.

1. Podržte stisknutou klávesu **Ctrl** klíče a přetáhněte prostředek do druhého souboru .rc. Například, přetáhněte **IDD_DIALOG1** z `Source1.rc` k `Source2.rc`.

   > [!NOTE]
   > Přetažení prostředku bez podržení **Ctrl** klíč přesunu prostředku místo jeho kopírování.

## <a name="to-copy-resources-using-copy-and-paste"></a>Kopírování prostředků pomocí kopírování a vložení

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků, ve který #zahrnuje konce souboru mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například Source1.rc a Source2.rc.

1. Ve zdrojovém souboru, ze kterého chcete kopírovat prostředek (například `Source1.rc`), klikněte pravým tlačítkem na prostředek a zvolte **kopírování** z místní nabídky.

1. Klikněte pravým tlačítkem na soubor prostředků, do které chcete vložit prostředku (například `Source2.rc`). Zvolte **vložit** z místní nabídky.

   > [!NOTE]
   > Nelze přetáhnout a vyřadit, kopírování, vyjmutí nebo vložte mezi soubory prostředků v projektu (**zobrazení prostředků**) a samostatné .rc soubory (ty otevřít v systému windows dokumentu). Můžete to udělat v předchozích verzích produktu.

   > [!NOTE]
   > Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor, Visual C++ změnit hodnotu symbolu přenesené prostředků nebo název symbolu a hodnota při kopírování do nového souboru.

## <a name="to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Změna jazyka nebo podmínky prostředku během kopírování (C++)

Při kopírování v prostředku, můžete změnit jeho vlastnost jazyka vlastnost podmínka nebo obojí.

- Určuje jazyk prostředku přesně to, jazyk prostředku. Jazyk používá [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) vám pomůže identifikovat prostředek, pro který potřebujete. (Ale prostředky mohou mít rozdíly pro jednotlivé jazyky, které se vztahují na text, například akcelerátory, které může fungovat jenom na použití japonské klávesnice nebo rastrový obrázek, který může být pouze vhodné pro čínštinu lokalizované sestavení.)

- Podmínky prostředku je definovaný symbol, který určuje podmínku, pod kterým se má použít tento konkrétní kopie prostředku.

Jazyk a podmínky prostředku jsou uvedeny v závorkách za názvem prostředku v okně pracovního prostoru. V tomto příkladu používá prostředek s názvem IDD_AboutBox finština jako svůj jazyk a jeho stav je XX33.

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Kopírovat existující prostředek a změnit jeho jazyka nebo podmínky

1. V souboru .rc nebo v [zobrazení prostředků](../windows/resource-view-window.md) okna, klikněte pravým tlačítkem na prostředek, které chcete kopírovat.

1. Zvolte **vložit kopii** z místní nabídky.

1. V **vložit kopii prostředku** dialogové okno:

   - Pro **jazyk** seznamu, vyberte jazyk.

   - V **podmínku** zadejte podmínku.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
[Postupy: Otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
