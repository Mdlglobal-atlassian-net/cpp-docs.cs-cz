---
title: Prostředek symboly – dialogové okno (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourcesymbols
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
ms.openlocfilehash: 156b531bfcedca70c930d77773d3a308735735f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483509"
---
# <a name="resource-symbols-dialog-box-c"></a>Prostředek symboly – dialogové okno (C++)

**Symbolů prostředků** C++ dialogové okno umožňuje přidat nový prostředek symboly, symboly, které se zobrazí, nebo přejděte do umístění ve zdrojovém kódu, pokud symbol je používán změnit.

- **Jméno**

   Zobrazí název symbolu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).

- **Hodnota**

   Zobrazí číselnou hodnotu symbolu. Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).

- **Používá**

   Pokud je vybráno, určuje, že symbol je používán jeden nebo více prostředků. Prostředek nebo prostředky jsou uvedeny v seznamu používá pole.

- **Zobrazit jen pro čtení symbolů**

   Pokud je vybráno, zobrazí prostředky jen pro čtení. Ve výchozím nastavení **Symbol prostředku** dialogové okno zobrazí jenom upravitelné prostředky v souboru skriptu prostředku, ale tato možnost aktivní, lze měnit prostředky se zobrazí tučným písmem a prostředky jen pro čtení se zobrazí ve formátu prostého textu.

- **Používá**

   Zobrazí prostředek nebo prostředky pomocí symbolu vybrali v seznamu symboly. Přejděte do editoru pro daný prostředek vyberte prostředek v **používá** pole a klikněte na tlačítko **zobrazit použití**. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).

- **Nový**

   Otevře **nový Symbol** dialogové okno, které vám umožní definovat název a v případě potřeby, hodnotu pro nový identifikátor symbolické prostředků. Další informace najdete v tématu [vytváření nových symbolů](../windows/creating-new-symbols.md).

- **Změna**

   Otevře **změnit Symbol** dialogové okno, které vám umožní změnit název nebo hodnotu symbolu. Pokud je symbol pro ovládací prvek nebo prostředek používá, symbol lze změnit pouze z editoru odpovídající prostředek. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).

- **Použití zobrazení**

   Otevře se na prostředek, který obsahuje symbol v editoru odpovídající prostředek. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)