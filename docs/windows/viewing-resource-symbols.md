---
title: Zobrazení symbolů prostředků (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
helpviewer_keywords:
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 4bcc06d9-7d36-486a-8a37-71da0541643c
ms.openlocfilehash: e61269261fc9172288f1edf58419009178c755d9
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763970"
---
# <a name="viewing-resource-symbols"></a>Zobrazení symbolů prostředků

**Symbolů prostředků** C++ dialogové okno umožňuje přidat nový prostředek symboly, symboly, které se zobrazí, nebo přejděte do umístění ve zdrojovém kódu, pokud symbol je používán změnit.

Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Název**|Zobrazí název symbolu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).|
|**Hodnota**|Zobrazí číselnou hodnotu symbolu. Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).|
|**Používá**|Pokud je vybráno, určuje, že symbol je používán jeden nebo více prostředků. Prostředek nebo prostředky jsou uvedeny v seznamu používá pole.|
|**Zobrazit jen pro čtení symbolů**|Pokud je vybráno, zobrazí prostředky jen pro čtení. Ve výchozím nastavení **Symbol prostředku** dialogové okno zobrazí jenom upravitelné prostředky v souboru skriptu prostředku, ale tato možnost aktivní, lze měnit prostředky se zobrazí tučným písmem a prostředky jen pro čtení se zobrazí ve formátu prostého textu.|
|**Používá**|Zobrazí prostředek nebo prostředky pomocí symbolu vybrali v seznamu symboly. Přejděte do editoru pro daný prostředek vyberte prostředek v **používá** pole a klikněte na tlačítko **zobrazit použití**. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).|
|**Nové**|Otevře **nový Symbol** dialogové okno, které vám umožní definovat název a v případě potřeby, hodnotu pro nový identifikátor symbolické prostředků. Další informace najdete v tématu [vytváření nových symbolů](../windows/creating-new-symbols.md).|
|**Změna**|Otevře **změnit Symbol** dialogové okno, které vám umožní změnit název nebo hodnotu symbolu. Pokud je symbol pro ovládací prvek nebo prostředek používá, symbol lze změnit pouze z editoru odpovídající prostředek. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).|
|**Použití zobrazení**|Otevře se na prostředek, který obsahuje symbol v editoru odpovídající prostředek. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).|

## <a name="to-view-resource-symbols"></a>K zobrazení symbolů prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. Vyberte **symbolů prostředků** z místní nabídky do zobrazení tabulky symbolů prostředků v **symbolů prostředků** dialogové okno.

   > [!NOTE]
   > Předdefinované symboly najdete **zobrazit jen pro čtení symbolů** zaškrtávací políčko.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)