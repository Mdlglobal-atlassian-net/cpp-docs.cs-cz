---
title: Kreslení v zobrazení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc716800c35aa922f7912f586d6e5b8429593615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346162"
---
# <a name="drawing-in-a-view"></a>Kreslení v zobrazení
Téměř všechny kreslení v aplikaci dojde v zobrazení `OnDraw` členská funkce, které je nutné přepsat ve třídě zobrazení. (Výjimkou je myši kreslení, popsané v [interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md).) Vaše `OnDraw` přepsání:  
  
1.  Získá data voláním dokumentu členské funkce, které zadáte.  
  
2.  Zobrazí data pomocí volání členské funkce objektu kontextu zařízení, který předává rozhraní `OnDraw`.  
  
 Při změně dokumentu dat nějakým způsobem, musí být zobrazení překreslen tak, aby odrážely změny. Obvykle se to stane, když uživatel provede změny prostřednictvím zobrazení na dokumentu. V takovém případě zobrazení volá dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) – členská funkce oznámit všechna zobrazení dokumentem aktualizovat sami. `UpdateAllViews` volá jednotlivých zobrazení [OnUpdate](../mfc/reference/cview-class.md#onupdate) – členská funkce. Výchozí implementaci `OnUpdate` by způsobila neplatnost zobrazení celého klienta. Je možné přepsat jeho zneplatní pouze tyto oblasti klientské oblasti, které jsou mapovány na změněné části dokumentu.  
  
 `UpdateAllViews` Funkce člena třídy **CDocument** a `OnUpdate` funkce člena třídy `CView` umožňují předávat informace, které popisují, které části dokumentu byly upraveny. Tento mechanismus "pomocný parametr" umožňuje omezit k oblasti, která musí ho překreslit zobrazení. `OnUpdate` přebírá dva argumenty "pomocný parametr". První, `lHint`, typu **LPARAM**, vám umožní předat žádná data, která se vám líbí, zatímco druhý, `pHint`, typu `CObject`*, vám umožní předat ukazatel u všech objektů odvozených od `CObject`.  
  
 Při zobrazení stává neplatným, systém Windows odešle ji `WM_PAINT` zprávy. Zobrazení [OnPaint](../mfc/reference/cwnd-class.md#onpaint) obslužné rutiny funkce reaguje na zprávy vytvoření třídy kontextu zařízení objektu [CPaintDC](../mfc/reference/cpaintdc-class.md) a volání do zobrazení `OnDraw` – členská funkce. Za normálních okolností nemáte zápis přepsání `OnPaint` funkce obslužné rutiny.  
  
 A [kontextu zařízení](../mfc/device-contexts.md) je datová struktura Windows, který obsahuje informace o kreslení atributy zařízení, například zobrazení nebo tiskárnu. Všechny kreslení volání prostřednictvím objektu kontextu zařízení. Pro kreslení na obrazovce `OnDraw` je předána `CPaintDC` objektu. Pro kreslení na tiskárnu, je předaná [CDC](../mfc/reference/cdc-class.md) objekt nastavení pro aktuální tiskárny.  
  
 Kód pro kreslení v zobrazení nejprve načte ukazatel dokumentu, a poté provede vykreslení volání kontextu zařízení. Následující jednoduchý `OnDraw` příklad znázorňuje proces:  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 V tomto příkladu můžete definovat `GetData` fungovat jako člen skupiny odvození dokumentové třídy.  
  
 V příkladu se vytiskne ať řetězec získá z dokumentu, na střed v zobrazení. Pokud `OnDraw` volání je pro vykreslování obrazovky `CDC` objekt předaný v `pDC` je `CPaintDC` již volána jehož konstruktor `BeginPaint`. Volání funkce vykreslování jsou vytvářeny pomocí ukazatele kontextu zařízení. Informace o kontextech zařízení a kreslení volání najdete v tématu třídy [CDC](../mfc/reference/cdc-class.md) v *odkaz knihovny MFC* a [práce s objekty oken](../mfc/working-with-window-objects.md).  
  
 Další příklady, jak napsat `OnDraw`, najdete v článku [MFC ukázky](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení](../mfc/using-views.md)

