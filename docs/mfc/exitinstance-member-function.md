---
title: "ExitInstance – členská funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99898a5e80c3f487c7f53fe81d13d3d1eb55ebd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md) nazývá pokaždé, když kopie aplikace ukončí, obvykle v důsledku opuštění aplikace uživatele.  
  
 Přepsání `ExitInstance` Pokud potřebujete čištění zvláštní zpracování, např. tím uvolní prostředky rozhraní GDI grafiky zařízení nebo rušení přidělení paměti při spuštění programu. Čištění standardní položek, jako jsou dokumenty a zobrazení, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění speciální čištění, které jsou specifické pro tyto objekty.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
