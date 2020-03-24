---
title: 'Postupy: vytváření symbolů (C++)'
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
ms.openlocfilehash: 1c69e8878885acd80c285691fb0861a476af03ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160512"
---
# <a name="how-to-create-symbols-c"></a>Postupy: vytváření symbolů (C++)

Když začínáte nový projekt, může být užitečné, abyste před vytvořením prostředků, ke kterým se přiřadíte, mohli namapovat názvy symbolů, které potřebujete.

> [!NOTE]
> Pokud projekt ještě neobsahuje soubor. RC, přečtěte si téma [Postupy: vytváření prostředků](../windows/how-to-create-a-resource-script-file.md).

Dialogové okno **symboly prostředků** umožňuje přidat nové symboly prostředků, změnit zobrazené symboly nebo přeskočit na umístění ve zdrojovém kódu, kde se symbol používá.

Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|--------------------------|------------------------------------------|
|**Název**|Zobrazuje název symbolu.<br/><br/>Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).|
|**Hodnota**|Zobrazí číselnou hodnotu symbolu.<br/><br/>Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).|
|**Používáno**|Je-li vybrána tato možnost, určuje, že symbol je používán jedním nebo více prostředky.<br/><br/>Prostředek nebo prostředky jsou uvedeny v poli **použito** v.|
|**Zobrazit symboly jen pro čtení**|Když se tato možnost vybere, zobrazí se prostředky jen pro čtení.<br/><br/>Ve výchozím nastavení se v dialogovém okně **symbol prostředku** zobrazí v souboru skriptu prostředků pouze upravitelné prostředky, ale při výběru této možnosti se v textu zobrazí tučné zdroje a v prostém textu se zobrazí zdroje jen pro čtení.|
|**Využíval**|Zobrazí prostředek nebo prostředky pomocí symbolu vybraného v seznamu symboly.<br/><br/>Chcete-li přejít do editoru daného prostředku, vyberte prostředek v poli **používáno** a zvolte možnost **Zobrazit použití**.|
|**New**|Otevře dialogové okno **Nový symbol** , ve kterém můžete definovat název a v případě potřeby zadat hodnotu pro nový symbolický identifikátor prostředku.|
|**Mění**|Otevře dialogové okno **změnit symbol** , které umožňuje změnit název nebo hodnotu symbolu.<br/><br/>Pokud je symbol určen pro ovládací prvek nebo prostředek, lze symbol změnit pouze z odpovídajícího editoru prostředků. Další informace najdete v tématu [Správa symbolů](../windows/changing-unassigned-symbols.md).|
|**Zobrazit použití**|Otevře prostředek, který obsahuje symbol v odpovídajícím editoru prostředků.|

## <a name="create-symbols"></a>Vytváření symbolů

### <a name="to-create-a-new-symbol"></a>Vytvoření nového symbolu

1. V dialogovém okně **symboly prostředků** klikněte na tlačítko **Nový**.

1. Do pole **název** zadejte název symbolu.

1. Přijměte přiřazenou hodnotu symbolu nebo zadejte novou hodnotu do pole **hodnota** .

1. Vyberte **OK** , chcete-li přidat nový symbol do seznamu symbolů.

> [!NOTE]
> Pokud zadáte název symbolu, který již existuje, zobrazí se okno se zprávou informující o tom, že symbol s tímto názvem je již definován. Nemůžete definovat dva nebo více symbolů se stejným názvem, ale můžete definovat různé symboly se stejnou číselnou hodnotou.

## <a name="to-view-resource-symbols"></a>Zobrazení symbolů prostředků

V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem myši na soubor *. RC* a vyberte možnost **symboly prostředků** pro zobrazení tabulky symbolů prostředků v dialogovém okně **symboly prostředků** .

> [!NOTE]
> Pokud chcete zobrazit předdefinované symboly, zaškrtněte políčko **Zobrazit symboly jen pro čtení** .

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>Otevření editoru prostředků pro daný symbol

Když procházíte symboly v **symbolech prostředků**, budete možná chtít získat další informace o použití konkrétního symbolu. Tlačítko **Zobrazit použití** poskytuje rychlý způsob, jak tyto informace získat.

1. V dialogovém okně **symboly prostředků** v poli **název** vyberte symbol.

1. V poli **používáno** vyberte typ prostředku, který vás zajímá.

1. Vyberte tlačítko **Zobrazit použít** .

   Prostředek se zobrazí v příslušném okně editoru.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>
[Postupy: Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
