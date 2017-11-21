---
title: "ExitInstance – členská funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs: C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dc1710bbb6efd5bc48aa0b640c8e05747dce2e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce
[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) funkce člena třídy [CWinApp](../mfc/reference/cwinapp-class.md) nazývá pokaždé, když kopie aplikace ukončí, obvykle v důsledku opuštění aplikace uživatele.  
  
 Přepsání `ExitInstance` Pokud potřebujete čištění zvláštní zpracování, např. tím uvolní prostředky rozhraní GDI grafiky zařízení nebo rušení přidělení paměti při spuštění programu. Čištění standardní položek, jako jsou dokumenty a zobrazení, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění speciální čištění, které jsou specifické pro tyto objekty.  
  
## <a name="see-also"></a>Viz také  
 [CWinApp – Třída aplikace](../mfc/cwinapp-the-application-class.md)
