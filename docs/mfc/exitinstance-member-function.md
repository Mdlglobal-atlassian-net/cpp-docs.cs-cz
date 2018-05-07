---
title: ExitInstance – členská funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 954d2248061ec571d9d2ba8804c1f7c97275cbfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md) nazývá pokaždé, když kopie aplikace ukončí, obvykle v důsledku opuštění aplikace uživatele.  
  
 Přepsání `ExitInstance` Pokud potřebujete čištění zvláštní zpracování, např. tím uvolní prostředky rozhraní GDI grafiky zařízení nebo rušení přidělení paměti při spuštění programu. Čištění standardní položek, jako jsou dokumenty a zobrazení, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění speciální čištění, které jsou specifické pro tyto objekty.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
