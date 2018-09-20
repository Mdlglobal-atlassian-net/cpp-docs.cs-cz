---
title: MDI – skupiny se záložkami | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35113181a21a5ff265b12269f57ee853f6011abc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442159"
---
# <a name="mdi-tabbed-groups"></a>MDI – skupiny se záložkami

Funkci skupin s kartami (MDI interface) více dokumentů umožňuje více dokumentu aplikace (MDI interface) zobrazíte jeden nebo více oken s kartami (nebo skupiny systému windows s kartami, označované jako *– skupiny se záložkami*) v oblasti klienta MDI. Okna s kartami může být zarovnaný vodorovně nebo svisle. Pokud aplikace je hostitelem více než jedné skupiny s kartami MDI, tyto skupiny jsou odděleny příčky.

## <a name="features"></a>Funkce

Následující části jsou uvedené funkce skupin s kartami MDI:

- Aplikace může dynamicky vytvořit okna s kartami.

- Aplikace můžete zarovnat oken s kartami, vodorovně nebo svisle.

- Skupiny systému windows s kartami jsou odděleny příčky. Uživatel může změnit velikost skupin s kartami pomocí příčky.

- Uživatel můžete přetáhnout jednotlivé karty mezi skupinami.

- Uživatel můžete přetáhnout jednotlivé karty k vytvoření nové skupiny.

- Uživatel může přesunout karty nebo vytvářet nové skupiny pomocí místní nabídky.

- Aplikace můžete uložit a načíst rozložení oken s kartami.

- Aplikace můžete uložit a načíst seznam dokumentů MDI.

- Aplikace může přístup jednotlivých skupin s kartami a změnit jejich parametry.

### <a name="using-mdi-tabbed-groups"></a>Pomocí MDI – skupiny se záložkami

Zde jsou úkoly obvykle provádí pomocí skupin s kartami MDI:

- Chcete-li povolit skupin s kartami MDI pro hlavní okno rámce, zavolejte [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Druhý parametr této metody je instance `CMDITabInfo` třídy. Můžete použít výchozí parametry nebo je upravit před voláním `CMDIFrameWndEx::EnableMDITabbedGroups`.

- Pokud chcete upravit vlastnosti skupiny s kartami MDI v době běhu, vytvořit nebo změnit `CMDITabInfo` objektu a volání `CMDIFrameWndEx::EnableMDITabbedGroups` znovu

- Získat seznam MDI s kartami windows, zavolejte `CMDIFrameWndEx::GetMDITabGroups`.

- Chcete-li vytvořit novou skupinu s kartami MDI vedle active skupina s kartami, zavolejte `CMDIFrameWndEx::MDITabNewGroup`.

- Chcete-li posunout zaměření pro vstup do předchozí nebo další okna skupina s kartami, zavolejte `CMDIFrameWndEx::MDITabMoveToNextGroup`.

- Určuje, jestli je okno členem MDI – skupiny volání se záložkami `CMDIFrameWndEx::IsMemberOfMDITabGroup`.

- Chcete-li zjistit, jestli jsou povolené karet MDI nebo skupin s kartami MDI pro hlavní okno rámce, zavolejte `CMDIFrameWndEx::AreMDITabs`. Chcete-li zjistit, zda jsou povoleny skupin s kartami MDI, zavolejte `CMDIFrameWndEx::IsMDITabbedGroup`.

- Chcete-li zobrazit místní nabídku, když uživatel klepne na kartu nebo přesune do jiné skupiny s kartami MDI, přepište `CMDIFrameWndEx::OnShowMDITabContextMenu` v `CMDIFrameWndEx`-odvozené třídy. Pokud tuto metodu nelze implementovat, aplikace nebude zobrazení místní nabídky.

- Chcete-li uložit rozložení skupin s kartami MDI v aplikaci, zavolejte `CMDIFrameWndEx::SaveMDIState`. Načíst dříve uložený MDI – skupiny profilu se záložkami, zavolejte `CMDIFrameWndEx::LoadMDIState`. Můžete také volat tyto metody k načtení nebo uložení seznamu otevřených dokumentů v aplikaci MDI. Další informace o ukládání a načítání stavu MDI, naleznete v tématu [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[CMDIFrameWndEx – třída](../mfc/reference/cmdiframewndex-class.md)<br/>
[CMDIChildWndEx – třída](../mfc/reference/cmdichildwndex-class.md)<br/>
[CMDITabInfo – třída](../mfc/reference/cmditabinfo-class.md)
