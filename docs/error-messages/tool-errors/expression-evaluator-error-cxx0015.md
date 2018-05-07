---
title: CXX0015 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 945dbda4759fa2989acb0411d1a3216a5e9a036c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0015"></a>Chyba při vyhodnocování výrazu CXX0015
výraz je příliš složitý (přetečení zásobníku)  
  
 Zadaný výraz je příliš složitý nebo vnořené příliš hluboko pro velikost úložiště, které jsou k dispozici pro vyhodnocovací filtr výrazů C.  
  
 Přetečení obvykle dochází z důvodu příliš mnoho čekající výpočty.  
  
 Změna uspořádání výraz tak, aby jednotlivé komponenty výraz může být vyhodnocen jako jeho zjištění, namísto nutnosti počkejte dalších částí výraz, který má být vypočítána.  
  
 Výraz rozdělte do více příkazů.  
  
 Tato chyba je stejný jako CAN0015.