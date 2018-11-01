---
title: 'Postupy: použití šablon prostředků (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- language-specific template files [C++]
- resource templates
- resources [C++], creating
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
ms.openlocfilehash: d92579214dec96ea67537b4eb37e4554054d411d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577382"
---
# <a name="how-to-use-resource-templates-c"></a>Postupy: použití šablon prostředků (C++)

Prostředek šablony je vlastní prostředek, který jste uložili jako soubor s příponou .rct. Šablony prostředků pak může sloužit jako výchozí bod pro vytvoření dalších prostředků. Šablony prostředků ušetřit čas při vývoji další prostředky nebo skupiny prostředků, které sdílejí funkce, jako je standardní ovládací prvky a další opakované prvků. Například můžete chtít zahrnout tlačítko Nápověda a ikona logo společnosti v několika dialogových oknech. Provedete to tak rychle, vytvořte novou šablonu pole dialogové okno a přizpůsobit pomocí loga a na tlačítko Nápověda.

Jakmile jste upravili šablony prostředků, musí svoje změny uložíte ve složce šablony (nebo jakékoli umístění, zadaný v cestě k zahrnutí) tak, aby nového prostředku šablony se zobrazí v části jeho typ prostředku v [přidat prostředek – dialogové okno](../windows/add-resource-dialog-box.md). Potom můžete nového prostředku šablony tak často, podle potřeby.

> [!NOTE]
> Soubory šablon specifické pro jazyk můžete umístit v podadresářích adresáře hlavní šablony. Například můžete umístit soubory šablon anglické v \\< adresář prostředků šablony\>\1033.

### <a name="to-create-a-template-for-resources"></a>Vytvoření šablony pro prostředky

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt.

2. V místní nabídce zvolte **přidat**, pak klikněte na tlačítko **přidat novou položku**.

3. V **přidat novou položku** v dialogu **šablony:** podokně zvolte **soubor šablony zdrojů (.rct)**.

4. Zadejte název a umístění souboru nového .rct a klikněte na tlačítko **otevřít**.

5. Nový soubor .rct se přidá do vašeho projektu a zobrazí se v **Průzkumníka řešení** pod **prostředky** složky.

   Můžete teď poklikejte na soubor .rct a otevřete ho v okně dokumentu a pak přidat prostředky do ní (klikněte pravým tlačítkem na soubor v okně dokumentu a zvolte **přidat prostředek** z místní nabídky). Můžete poté přizpůsobit tyto prostředky a uložte soubor .rct.

   > [!NOTE]
   > Při vytváření nového souboru RCT sady Visual Studio vyhledá ho v sadě Visual Studio 9.0\VC\VCResourceTemplates \Program Files\Microsoft, v sadě Visual Studio 9.0\VC\VCResourceTemplates \Program Files\Microsoft\\*LCID* () například 1033 pro angličtinu) *nebo* kdekoli [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md). Pokud dáváte přednost RCT soubory uložené v jiné složce souboru, například \My dokumentů, je potřeba jenom tuto složku přidat do cesty zahrnutí a sada Visual Studio se najít soubor RCT.

### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>Chcete-li převést existující soubor .rc do souboru .rct

1. [Otevřete soubor .rc jako samostatný soubor](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

2. Na **souboru** nabídky, klikněte na tlačítko **Uložit \< *váš název souboru*> jako**.

3. Zadejte umístění a klikněte na tlačítko **OK**.

### <a name="to-create-a-new-resource-from-a-template"></a>Chcete-li vytvořit nový prostředek ze šablony

1. V [zobrazení prostředků](../windows/resource-view-window.md) podokně klikněte pravým tlačítkem na soubor .rc a zvolte **přidat prostředek** z místní nabídky.

2. V **přidat prostředek** dialogového okna klikněte na symbol plus (**+**) u prostředků, rozbalte uzel zdroje a zobrazit všechny šablony, které jsou k dispozici pro daný prostředek.

3. Dvakrát klikněte na šablonu, kterou chcete použít.

4. Přidání prostředku upravte podle potřeby v jeho editor prostředků.

   Editor prostředků automaticky poskytuje jedinečné prostředku. Můžete zkontrolovat, jestli [vlastnosti prostředku](../windows/changing-the-properties-of-a-resource.md) podle potřeby.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)