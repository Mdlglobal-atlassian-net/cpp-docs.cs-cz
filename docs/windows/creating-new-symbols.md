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
ms.openlocfilehash: 01b810d162da4d59c2044fe02a1da5c0929d41b9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320598"
---
# <a name="how-to-create-symbols-c"></a>Postupy: Vytvoření symboly (C++)

Když začínáte nový projekt, možná bude vhodné ke zmapování názvy symbolů, které budete potřebovat ještě před vytvořením prostředků, které budete mít přiřazenou.

**Symbolů prostředků** C++ dialogové okno umožňuje přidat nový prostředek symboly, symboly, které se zobrazí, nebo přejděte do umístění ve zdrojovém kódu, pokud symbol je používán změnit.

Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|--------------------------|------------------------------------------|
|**Název**|Zobrazí název symbolu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).|
|**Hodnota**|Zobrazí číselnou hodnotu symbolu. Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).|
|**Používá**|Pokud je vybráno, určuje, že symbol je používán jeden nebo více prostředků. Prostředek nebo prostředky jsou uvedeny v seznamu používá pole.|
|**Zobrazit jen pro čtení symbolů**|Pokud je vybráno, zobrazí prostředky jen pro čtení. Ve výchozím nastavení **Symbol prostředku** dialogové okno zobrazí jenom upravitelné prostředky v souboru skriptu prostředku, ale tato možnost aktivní, lze měnit prostředky se zobrazí tučným písmem a prostředky jen pro čtení se zobrazí ve formátu prostého textu.|
|**Používá**|Zobrazí prostředek nebo prostředky pomocí symbolu vybrali v seznamu symboly. Přejděte do editoru pro daný prostředek vyberte prostředek v **používá** pole a tlačítko **zobrazit použití**.|
|**Nové**|Otevře **nový Symbol** dialogové okno, které vám umožní definovat název a v případě potřeby, hodnotu pro nový identifikátor symbolické prostředků.|
|**Změna**|Otevře **změnit Symbol** dialogové okno, které vám umožní změnit název nebo hodnotu symbolu. Pokud je symbol pro ovládací prvek nebo prostředek používá, symbol lze změnit pouze z editoru odpovídající prostředek. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).|
|**Použití zobrazení**|Otevře se na prostředek, který obsahuje symbol v editoru odpovídající prostředek.|

## <a name="create-symbols"></a>Vytváření symbolů

### <a name="to-create-a-new-symbol"></a>Chcete-li vytvořit nový symbol

1. V **symbolů prostředků** dialogového okna zvolte **nový**.

1. V **název** zadejte název symbolu.

1. Přijmout hodnotu přiřazenou symbolu nebo zadejte novou hodnotu **hodnotu** pole.

1. Vyberte **OK** přidáte nový symbol do seznamu symbol.

> [!NOTE]
> Pokud zadáte název symbolu, který již existuje, zobrazí se okno se zprávou s informacemi o tom, že je již definován symbol s tímto názvem. Nejde definovat dvě nebo víc symbolů se stejným názvem, ale můžete definovat různé symbolů se stejnou číselnou hodnotu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md) a [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).

### <a name="to-view-resource-symbols"></a>K zobrazení symbolů prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. Vyberte **symbolů prostředků** z místní nabídky do zobrazení tabulky symbolů prostředků v **symbolů prostředků** dialogové okno.

   > [!NOTE]
   > Předdefinované symboly najdete **zobrazit jen pro čtení symbolů** zaškrtávací políčko.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Chcete-li otevřít editor prostředků pro daný symbol

Při procházení symbolů v **symbolů prostředků**, můžete další informace o způsobu použití určitého symbolu. **Zobrazit použití** tlačítko poskytuje rychlý způsob, jak získat tyto informace.

#### <a name="to-move-to-the-resource-editor-where-a-symbol-is-being-used"></a>Přejděte do editoru prostředků, ve kterém se používá symbol

1. Vyberte symbol ve **název** pomocí boxingu **symbolů prostředků** dialogové okno.

1. V **používá** , vyberte typ prostředku, který vás zajímá.

1. Vyberte **zobrazit použití** tlačítko.

   Prostředek se zobrazí v okně editor odpovídající.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Identifikátory prostředků (symbolů)](../windows/symbols-resource-identifiers.md)<br/>
[Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>