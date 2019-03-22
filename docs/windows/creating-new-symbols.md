---
title: 'Postupy: Vytvoření symboly (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: c2e2f67a6547b05fca198a54b13776a1d3fafecf
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328919"
---
# <a name="how-to-create-symbols-c"></a>Postupy: Vytvoření symboly (C++)

Když začínáte nový projekt, možná bude vhodné ke zmapování názvy symbolů, které budete potřebovat ještě před vytvořením prostředků, které budete mít přiřazenou.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [jak: Vytvoření prostředků](../windows/how-to-create-a-resource-script-file.md).

**Symbolů prostředků** dialogové okno umožňuje přidat nový prostředek symboly, symboly, které se zobrazí, nebo přejděte do umístění ve zdrojovém kódu, pokud symbol je používán změnit.

Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|--------------------------|------------------------------------------|
|**Název**|Zobrazí název symbolu.<br/><br/>Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).|
|**Hodnota**|Zobrazí číselnou hodnotu symbolu.<br/><br/>Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).|
|**Používá**|Pokud je vybráno, určuje, že symbol je používán jeden nebo více prostředků.<br/><br/>Prostředek nebo prostředky jsou uvedeny v **používané** pole.|
|**Zobrazit jen pro čtení symbolů**|Pokud je vybráno, zobrazí prostředky jen pro čtení.<br/><br/>Ve výchozím nastavení **Symbol prostředku** dialogové okno zobrazí jenom upravitelné prostředky v souboru skriptu prostředku, ale tato možnost aktivní, lze měnit prostředky se zobrazí tučným písmem a prostředky jen pro čtení se zobrazí ve formátu prostého textu.|
|**Používá**|Zobrazí prostředek nebo prostředky pomocí symbolu vybrali v seznamu symboly.<br/><br/>Přejděte do editoru pro daný prostředek vyberte prostředek v **používané** pole a tlačítko **zobrazit použití**.|
|**Nové**|Otevře **nový Symbol** dialogové okno, které vám umožní definovat název a v případě potřeby, hodnotu pro nový identifikátor symbolické prostředků.|
|**Změna**|Otevře **změnit Symbol** dialogové okno, které vám umožní změnit název nebo hodnotu symbolu.<br/><br/>Pokud je symbol pro ovládací prvek nebo prostředek používá, symbol lze změnit pouze z editoru odpovídající prostředek. Další informace najdete v tématu [spravovat symboly](../windows/changing-unassigned-symbols.md).|
|**Použití zobrazení**|Otevře se na prostředek, který obsahuje symbol v editoru odpovídající prostředek.|

## <a name="create-symbols"></a>Vytváření symbolů

### <a name="to-create-a-new-symbol"></a>Chcete-li vytvořit nový symbol

1. V **symbolů prostředků** dialogového okna zvolte **nový**.

1. V **název** zadejte název symbolu.

1. Přijmout hodnotu přiřazenou symbolu nebo zadejte novou hodnotu **hodnotu** pole.

1. Vyberte **OK** přidáte nový symbol do seznamu symbol.

> [!NOTE]
> Pokud zadáte název symbolu, který již existuje, zobrazí se okno se zprávou s informacemi o tom, že je již definován symbol s tímto názvem. Nejde definovat dvě nebo víc symbolů se stejným názvem, ale můžete definovat různé symbolů se stejnou číselnou hodnotu.

## <a name="to-view-resource-symbols"></a>K zobrazení symbolů prostředků

V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na váš *.rc* a vyberte možnost **symbolů prostředků** zobrazení tabulky symbolů prostředků v **symbolů prostředků**dialogové okno.

> [!NOTE]
> Předdefinované symboly najdete **zobrazit jen pro čtení symbolů** zaškrtávací políčko.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Chcete-li otevřít editor prostředků pro daný symbol

Při procházení symbolů v **symbolů prostředků**, můžete další informace o způsobu použití určitého symbolu. **Zobrazit použití** tlačítko poskytuje rychlý způsob, jak získat tyto informace.

1. V **symbolů prostředků** dialogovém **název** , vyberte symbol.

1. V **používá** , vyberte typ prostředku, který vás zajímá.

1. Vyberte **zobrazit použití** tlačítko.

   Prostředek se zobrazí v okně editor odpovídající.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>
[Postupy: Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>