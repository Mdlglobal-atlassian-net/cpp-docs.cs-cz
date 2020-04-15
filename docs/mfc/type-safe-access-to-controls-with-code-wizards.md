---
title: Typově bezpečný přístup k ovládacím prvkům s průvodci kódem
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370919"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům s průvodci kódem

Pokud jste obeznámeni s funkcemi DDX, můžete použít Control vlastnost v [Přidat členské proměnné Průvodce](../ide/add-member-variable-wizard.md) k vytvoření typu bezpečný přístup. Tento přístup je jednodušší než vytváření ovládacích prvků bez průvodců kódem.

Pokud jednoduše chcete přístup k hodnotě ovládacího prvku, DDX poskytuje. Pokud chcete udělat více než přístup k hodnotě ovládacího prvku, přidejte do třídy dialogu pomocí Průvodce přidáním členské proměnné odpovídající třídy. Připojte tuto členovou proměnnou k vlastnosti Control.

Členské proměnné mohou mít vlastnost Control namísto vlastnosti Value. Value Vlastnost odkazuje na typ dat vrácených z `CString` ovládacího prvku, například nebo **int**. Vlastnost Control umožňuje přímý přístup k ovládacímu prvku prostřednictvím datového člena, jehož typ je jednou z tříd ovládacího prvku v knihovně MFC, například `CButton` nebo `CEdit`.

> [!NOTE]
> Pro daný ovládací prvek můžete, pokud chcete, mít více proměnných členů s Vlastností Value a maximálně jednu členovou proměnnou s vlastností Control. Na ovládací prvek může být mapován pouze jeden objekt knihovny MFC, protože více objektů připojených k ovládacímu prvku nebo jinému oknu by vedlo k nejednoznačnosti v mapě zpráv.

Tento objekt můžete použít k volání libovolné členské funkce pro objekt ovládacího prvku. Tato volání ovlivňují ovládací prvek v dialogovém okně. Například pro ovládací prvek zaškrtávacího políčka reprezentovaného proměnnou *m_Checkbox*, typu `CButton`, můžete volat:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Zde členská proměnná *m_Checkbox* slouží stejnému účelu jako členská funkce `GetMyCheckbox` zobrazená v [Typově bezpečném přístupu k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md). Pokud zaškrtávací políčko není automatické zaškrtávací políčko, budete stále potřebovat obslužnou rutinu ve vaší třídě dialogu pro BN_CLICKED zpráva o oznamování ovládacího prvku při klepnutí na tlačítko.

Další informace o ovládacích prvcích naleznete v [tématu Controls](../mfc/controls-mfc.md).

## <a name="see-also"></a>Viz také

[Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)
