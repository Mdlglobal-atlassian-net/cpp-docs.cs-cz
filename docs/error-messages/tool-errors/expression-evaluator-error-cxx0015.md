---
title: "CXX0015 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0015
dev_langs: C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d6b04fd2b13b2acd9021dcd8e751a0b4cbefd166
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0015"></a>Chyba při vyhodnocování výrazu CXX0015
výraz je příliš složitý (přetečení zásobníku)  
  
 Zadaný výraz je příliš složitý nebo vnořené příliš hluboko pro velikost úložiště, které jsou k dispozici pro vyhodnocovací filtr výrazů C.  
  
 Přetečení obvykle dochází z důvodu příliš mnoho čekající výpočty.  
  
 Změna uspořádání výraz tak, aby jednotlivé komponenty výraz může být vyhodnocen jako jeho zjištění, namísto nutnosti počkejte dalších částí výraz, který má být vypočítána.  
  
 Výraz rozdělte do více příkazů.  
  
 Tato chyba je stejný jako CAN0015.