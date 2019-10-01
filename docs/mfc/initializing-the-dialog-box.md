---
title: Inicializace dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685630"
---
# <a name="initializing-the-dialog-box"></a>Inicializace dialogového okna

Po vytvoření dialogového okna a všech jeho ovládacích prvků, ale těsně před tím, než se zobrazí dialogové okno (z obou typů) na obrazovce, je volána členská funkce [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) objektu dialogového okna. V případě modálního dialogového okna se k tomu dojde během volání `DoModal`. Pro nemodální dialogové okno se při volání `Create` zavolá `OnInitDialog`. Pro inicializaci ovládacích prvků dialogového okna, jako je například nastavení počátečního textu textového pole, je obvykle nutné přepsat `OnInitDialog`. Je nutné volat členskou funkci `OnInitDialog` základní třídy `CDialog` z přepsání `OnInitDialog`.

Pokud chcete nastavit barvu pozadí dialogového okna (a všechny ostatní dialogová okna v aplikaci), přečtěte si téma [Nastavení barvy pozadí dialogového okna](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Další informace najdete v tématech

[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)
