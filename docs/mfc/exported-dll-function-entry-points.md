---
title: Vstupní body exportované funkce DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: 8b84209833fee42ec8ebdd1fdea7a9229decad9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463320"
---
# <a name="exported-dll-function-entry-points"></a>Vstupní body exportované funkce DLL

Exportované funkce knihovny DLL, použijte [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) – makro zajistit správné globální stav při přechodu z modulu DLL knihovnou DLL volající aplikace.

Po zavolání toto makro nastaví `pModuleState`, ukazatel `AFX_MODULE_STATE` struktury obsahující globální data pro modul, jako stavu efektivní modulu pro zbývající z nadřazeného oboru funkce. Do odchodu obor obsahující makra, se automaticky obnoví předchozí stav efektivní modulu.

Tento přechod je dosáhnout konstrukcí instance `AFX_MODULE_STATE` třídy v zásobníku. V konstruktoru, tato třída získá ukazatel na aktuální stav modulu a uloží je v členské proměnné a pak nastaví `pModuleState` jako nový stav efektivní modulu. Tato třída ve svém destruktoru obnoví ukazatel uložené v jeho členskou proměnnou jako efektivní modulu stavu.

Pokud máte exportované funkce, jako je ten, který spustí dialogové okno v knihovně DLL, budete muset přidejte následující kód na začátek funkce:

[!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

To Zamění aktuální stav modulu se stavem vrácená [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate) až do konce v aktuálním oboru.

Problémy s prostředky v knihovnách DLL dojde, pokud `AFX_MANAGE_STATE` – makro se nepoužívá. Ve výchozím nastavení knihovna MFC používá k načtení šablony prostředků popisovač prostředku hlavní aplikace. Tato šablona je ve skutečnosti uložené v knihovně DLL. Hlavní příčinou je, že informace o stavu modulů knihovny MFC nebyl bylo změněno pomocí `AFX_MANAGE_STATE` – makro. Popisovač prostředku je obnovena ze stavu modulu MFC. Není přepnutí stavu modulu způsobí, že popisovač Chybný prostředek má být použit.

`AFX_MANAGE_STATE` není nutné převést do každé funkce v knihovně DLL. Například `InitInstance` je možné vyvolat v kódu knihovny MFC v aplikaci bez `AFX_MANAGE_STATE` protože MFC automaticky nastaven stav modulu před `InitInstance` a pak přepínače ji zpět po `InitInstance` vrátí. Totéž platí pro všechny obslužné rutiny mapování zprávy. Regulární knihovny DLL MFC ve skutečnosti mít speciální hlavní okno procedury, která automaticky přepne před směrováním jakákoliv zpráva o stavu modulu.

## <a name="see-also"></a>Viz také

[Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

