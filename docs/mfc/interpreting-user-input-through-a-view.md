---
title: Interpretace vstupu uživatele prostřednictvím zobrazení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e3ade658046ad789a92bce044d12e5a6e76f7ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349426"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretace vstupu uživatele prostřednictvím zobrazení
Jiné členské funkce zobrazení zpracovat a interpretovat všechny vstup uživatele. Obvykle nadefinujete obslužné rutiny zpráv členské funkce ve třídě zobrazení zpracování:  
  
-   Windows [zprávy](../mfc/messages.md) generované akce myši a klávesnice.  
  
-   [Příkazy](../mfc/user-interface-objects-and-command-ids.md) z nabídky, tlačítek panelu nástrojů a klávesy akcelerátoru.  
  
 Tato obslužná rutina zpráv členské funkce interpretovat následující akce jako zadávání dat, výběr nebo úpravy, včetně přesun dat do a ze schránky:  
  
-   Pohyb myši a kliknutí na nastavuje tažením a poklikáním  
  
-   Stisknutí kláves  
  
-   Příkazy nabídky  
  
 Zprávy, které Windows zobrazení popisovačů závisí na potřebách vaší aplikace.  
  
 [Zpracování a mapování témata zpráv](../mfc/message-handling-and-mapping.md) vysvětluje, jak přiřadit položek nabídky a jiné objekty uživatelského rozhraní pro příkazy a jak vytvořit vazbu mezi příkazy k funkcím obslužných rutin. [Zpracování a mapování témata zpráv](../mfc/message-handling-and-mapping.md) také vysvětluje, jak MFC směrování příkazů a odešle standardní zprávy Windows pro objekty, které obsahují obslužné rutiny pro ně.  
  
 Například aplikace může být nutné implementovat přímé myši kreslení v zobrazení. Vzorovou Scribble ukazuje způsob zpracování `WM_LBUTTONDOWN`, `WM_MOUSEMOVE`, a `WM_LBUTTONUP` zprávy a pokuste se spustit, v uvedeném pořadí a k kreslení úsek čáry. Na druhé straně může někdy musíte interpretovat kliknutí myši v zobrazení jako výběr. Vaše zobrazení `OnLButtonDown` obslužné rutiny funkce by určit, zda byl uživatel kreslení nebo výběr. Pokud vyberete, obslužná rutina by určit, zda byl kliknutím na možnost v rámci hranice některé objektu v zobrazení a pokud ano, změnit zobrazení zobrazíte objekt jako vybrané.  
  
 Zobrazení může také zpracovat určité nabídky příkazy jako ty, v nabídce Upravit vyjmout, kopírovat, vložit nebo odstranit vybraná data použití schránky. Tato obslužná rutina by volat, některé člena schránky související funkce třídy `CWnd` k přenosu vybraných dat položky do nebo ze schránky.  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení](../mfc/using-views.md)

