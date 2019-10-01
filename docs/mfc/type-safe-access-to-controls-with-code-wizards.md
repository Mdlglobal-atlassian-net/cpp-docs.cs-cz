---
title: Typově bezpečný přístup k ovládacím prvkům s průvodci kódem
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: fefa722209d37e2612201c4471e5764f9d71f27a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685045"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům s průvodci kódem

Pokud jste obeznámeni s funkcemi DDX, můžete použít vlastnost Control v [Průvodci přidáním členské proměnné](../ide/add-member-variable-wizard.md) pro vytvoření typově bezpečného přístupu. Tento přístup je snazší než vytváření ovládacích prvků bez průvodců kódem.

Pokud chcete jednoduše přístup k hodnotě ovládacího prvku, DDX ho poskytne. Chcete-li provést více než přístup k hodnotě ovládacího prvku, použijte Průvodce přidáním členské proměnné pro přidání členské proměnné příslušné třídy do vaší třídy dialogového okna. Připojte tuto členskou proměnnou k vlastnosti ovládacího prvku.

Členské proměnné mohou mít vlastnost ovládacího prvku namísto vlastnosti Value. Vlastnost Value odkazuje na typ dat vrácených z ovládacího prvku, například `CString` nebo **int**. Vlastnost Control umožňuje přímý přístup k ovládacímu prvku prostřednictvím datového členu, jehož typ je jedna z tříd ovládacích prvků v knihovně MFC, například `CButton` nebo `CEdit`.

> [!NOTE]
>  Pro daný ovládací prvek můžete, pokud chcete, mít více členských proměnných s vlastností value a maximálně jednu členskou proměnnou s vlastností Control. K ovládacímu prvku lze namapovat pouze jeden objekt knihovny MFC, protože více objektů připojených k ovládacímu prvku nebo jakémukoli jinému oknu by vedlo k nejednoznačnosti v mapě zpráv.

Tento objekt lze použít pro volání jakékoli členské funkce pro objekt ovládacího prvku. Taková volání ovlivňují ovládací prvek v dialogovém okně. Například pro ovládací prvek zaškrtávacího políčka reprezentovaný proměnnou *m_Checkbox*typu `CButton` můžete zavolat:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Zde členská proměnná *m_Checkbox* slouží ke stejnému účelu jako členská funkce `GetMyCheckbox` zobrazená v [typově bezpečném přístupu k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md). Pokud není zaškrtávací políčko Automatické, budete pro zprávu BN_CLICKED Control-Notification po kliknutí na tlačítko potřebovat obslužnou rutinu ve třídě dialog.

Další informace o ovládacích prvcích naleznete v tématu [Controls](../mfc/controls-mfc.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)
