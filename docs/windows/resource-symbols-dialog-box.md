---
title: Dialogové okno symboly prostředků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourcesymbols
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc4c6a749a5e3ef1835d959e7803ac6b6f4435ec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609816"
---
# <a name="resource-symbols-dialog-box"></a>Symboly prostředků – dialogové okno

**Symbolů prostředků** dialogové okno umožňuje přidat nový prostředek symboly, symboly, které se zobrazí, nebo přejděte do umístění ve zdrojovém kódu, pokud symbol je používán změnit.

**Jméno**  
Zobrazí název symbolu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md).

**Hodnota**  
Zobrazí číselnou hodnotu symbolu. Další informace najdete v tématu [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).

**Používá**  
Pokud je vybráno, určuje, že symbol je používán jeden nebo více prostředků. Prostředek nebo prostředky jsou uvedeny v seznamu používá pole.

**Zobrazit jen pro čtení symbolů**  
Pokud je vybráno, zobrazí prostředky jen pro čtení. Ve výchozím nastavení **Symbol prostředku** dialogové okno zobrazí jenom upravitelné prostředky v souboru skriptu prostředku, ale tato možnost aktivní, lze měnit prostředky se zobrazí tučným písmem a prostředky jen pro čtení se zobrazí ve formátu prostého textu.

**Používá**  
Zobrazí prostředek nebo prostředky pomocí symbolu vybrali v seznamu symboly. Přejděte do editoru pro daný prostředek vyberte prostředek v **používá** pole a klikněte na tlačítko **zobrazit použití**. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).

**Nový**  
Otevře **nový Symbol** dialogové okno, které vám umožní definovat název a v případě potřeby, hodnotu pro nový identifikátor symbolické prostředků. Další informace najdete v tématu [vytváření nových symbolů](../windows/creating-new-symbols.md).

**Změna**  
Otevře **změnit Symbol** dialogové okno, které vám umožní změnit název nebo hodnotu symbolu. Pokud je symbol pro ovládací prvek nebo prostředek používá, symbol lze změnit pouze z editoru odpovídající prostředek. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).

**Použití zobrazení**  
Otevře se na prostředek, který obsahuje symbol v editoru odpovídající prostředek. Další informace najdete v tématu [otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)