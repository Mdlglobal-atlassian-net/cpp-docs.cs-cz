---
title: Export knihoven DLL funkce vstupní body | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8e9ff08054fbef3f15283395d7eb150551926dc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928622"
---
# <a name="exported-dll-function-entry-points"></a>Vstupní body exportované funkce DLL
U exportovaných funkcí knihovny DLL, použijte [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) makro udržovat správné globální stav přepnutím z modulu DLL knihovny DLL je volající aplikace.  
  
 Při volání, nastaví tento makro `pModuleState`, ukazatel na `AFX_MODULE_STATE` struktura obsahující globální data modulu, jako stav efektivní modulu pro zbývající rozsah funkce. Při výstupu oboru obsahující makro, se automaticky obnoví předchozí stav efektivní modulu.  
  
 Tento přechod se dosahuje vytváření instance `AFX_MODULE_STATE` – třída v zásobníku. V jeho konstruktoru Tato třída získá ukazatel na aktuální stav modulu a ukládá je v členské proměnné a nastaví `pModuleState` jako nový stav efektivní modulu. Tato třída v jeho – destruktor obnoví ukazatele uložen v jeho členské proměnné stavu efektivní modulu.  
  
 Pokud máte exportované funkce, například ten, který spustí dialogové okno v knihovně DLL, budete muset přidejte následující kód do začátku funkce:  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]  
  
 To umožňuje přepnout aktuální stav modulu se stavem vrácená z [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate) až do konce aktuálního oboru.  
  
 Problémy s prostředky v knihovnách DLL dojde, pokud `AFX_MANAGE_STATE` makro nepoužívá. Ve výchozím nastavení používá MFC popisovač prostředku hlavní aplikace pro načtení šablony prostředků. Tato šablona je ve skutečnosti uložený v knihovně DLL. Hlavní příčinou je, že informace o stavu modulu MFC nebyl byla přepnuta pomocí `AFX_MANAGE_STATE` makro. Popisovač prostředku je obnovena ze stavu modulu MFC společnosti. Není přepnutí stavu modulu způsobí, že popisovač nesprávný prostředku, který se má použít.  
  
 `AFX_MANAGE_STATE` není nutné k uvedení do každé funkce v knihovně DLL. Například `InitInstance` je možné volat v MFC kód aplikace bez `AFX_MANAGE_STATE` protože MFC automaticky posune stav modulu před `InitInstance` a pak přepínače zpátky po `InitInstance` vrátí. Totéž platí pro všechny zprávy mapování obslužné rutiny. Regulární knihovny DLL MFC ve skutečnosti mít speciální hlavní okno procedury, která automaticky přepne stav modulu před směrování jakékoli zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

