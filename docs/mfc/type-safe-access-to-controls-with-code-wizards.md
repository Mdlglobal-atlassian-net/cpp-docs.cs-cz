---
title: Typově bezpečný přístup k ovládacím prvkům s průvodci kódem
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: bf3ecf3016fcc15bd4ada7a15208acd9a04ca0a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263803"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům s průvodci kódem

Pokud jste se seznámili s funkcemi DDX, můžete použít vlastnost ovládacího prvku [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) k vytvoření typově bezpečný přístup. Tento přístup je snazší než vytvoření ovládacím prvkům bez průvodců kódem.

Pokud chcete jednoduše přístup k hodnotě ovládacího prvku, poskytuje DDX ji. Pokud chcete více než přístup k hodnotě ovládacího prvku, přidání členské proměnné třídy odpovídající vlastní třídy dialogového okna pomocí Průvodce přidáním členské proměnné. Tato členská proměnná připojte k vlastnosti ovládacího prvku.

Proměnné členů může mít vlastnosti ovládacího prvku místo vlastnost Value. Vlastnost hodnota odkazuje na typu dat vrácených z ovládacího prvku, jako například `CString` nebo **int**. Vlastnosti ovládacího prvku umožňuje přímý přístup k řízení prostřednictvím datového člena, jehož typ je jednou z třídy ovládacích prvků v knihovně MFC, jako například `CButton` nebo `CEdit`.

> [!NOTE]
>  Pro daný ovládací prvek můžete, pokud chcete, mít více členské proměnné se hodnota vlastnosti a nejvýše jednu členskou proměnnou s vlastností ovládacího prvku. Může mít pouze jeden objekt knihovny MFC, které jsou namapované na ovládací prvek, protože více objektů, které jsou připojené k ovládací prvek nebo jiné okno by mohlo dojít k nejednoznačnost v mapování zprávy.

Tento objekt můžete volat jakékoli členské funkce pro objekt ovládacího prvku. Taková volání ovlivní ovládacího prvku v dialogovém okně. Například pro ovládací prvek zaškrtávací políčko reprezentována proměnnou *m_Checkbox*, typu `CButton`, lze volat:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Tady členskou proměnnou *m_Checkbox* slouží stejnému účelu jako členskou funkci `GetMyCheckbox` ukazuje [typově bezpečný přístup k ovládací prvky bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md). Pokud políčko není zaškrtnutí políčka automaticky, je stále třeba obslužnou rutinu ve vlastní třídy dialogového okna pro zprávu s oznámením ovládacího prvku BN_CLICKED po kliknutí na tlačítko.

Další informace o ovládacích prvcích najdete v tématu [ovládací prvky](../mfc/controls-mfc.md).

## <a name="see-also"></a>Viz také:

[Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)
