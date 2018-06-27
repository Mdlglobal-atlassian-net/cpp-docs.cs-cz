---
title: Typově bezpečný přístup k ovládacím prvkům s průvodci kódem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f86a8f22bae990261be5150755a26d50d4bef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950458"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Typově bezpečný přístup k ovládacím prvkům s průvodci kódem
Pokud jste obeznámeni s funkcemi DDX, můžete použít vlastnost ovládacího prvku v [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md) vytvořit typově bezpečný přístup. Tento přístup je jednodušší než vytváření ovládacím prvkům bez průvodců kódem.  
  
 Pokud chcete jednoduše přístup k ovládacím prvku hodnotu, poskytuje DDX ji. Pokud chcete získat přístup více než hodnota ovládacího prvku, použijte Průvodce přidáním členské proměnné přidání členské proměnné příslušné třídy do vlastní třídy dialogového okna. Tato proměnná člen připojte k vlastnosti ovládacího prvku.  
  
 Členské proměnné může mít vlastnost řídicí místo vlastnosti Value. Hodnota vlastnosti odkazuje na typ data vrácená z ovládacího prvku, například `CString` nebo **int**. Vlastnost ovládacího prvku umožňuje přímý přístup k řízení prostřednictvím datový člen, jejichž typ je jedním z třídy ovládacích prvků v prostředí MFC, jako například `CButton` nebo `CEdit`.  
  
> [!NOTE]
>  Pro daný ovládací prvek můžete, pokud chcete, máte několik členské proměnné se hodnota vlastnosti a maximálně jeden členské proměnné s vlastností ovládacího prvku. Může mít pouze jeden objekt MFC mapovat do ovládacího prvku, protože více objektů, které jsou připojené k prvku nebo libovolného jiného okna nezkopírujete, dojde k to nejednoznačnost v mapy zpráv.  
  
 Tento objekt můžete použít k volání funkce kteréhokoli člena pro objekt ovládacího prvku. Takové volání ovlivní ovládacího prvku v dialogovém okně. Například pro ovládací prvek zaškrtávací políčko reprezentována proměnné *m_Checkbox*, typu `CButton`, může volat:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 Zde členské proměnné *m_Checkbox* slouží ke stejnému účelu jako členskou funkci `GetMyCheckbox` ukazuje [typově bezpečný přístup k ovládacích prvků bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md). Pokud políčko není zaškrtnutí políčka automaticky, stále potřebovali byste obslužnou rutinu v vlastní třídy dialogového okna pro zprávu oznámení ovládacího prvku BN_CLICKED při kliknutí na tlačítko.  
  
 Další informace o ovládacích prvcích najdete v tématu [ovládací prvky](../mfc/controls-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Typově bezpečný přístup k ovládacím prvkům v dialogovém okně](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [Typově bezpečný přístup k ovládacím prvkům bez průvodců kódem](../mfc/type-safe-access-to-controls-without-code-wizards.md)

