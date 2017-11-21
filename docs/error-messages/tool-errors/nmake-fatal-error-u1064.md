---
title: "Závažná chyba nástroje NMAKE U1064 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1064
dev_langs: C++
helpviewer_keywords: U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 123b84922df702aad9dc391da1b83bfa81265fe0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1064"></a>Závažná chyba nástroje NMAKE U1064
Nebyl nalezen v souboru pravidel a není zadán žádný cíl.  
  
 Příkaz NMAKE nezadali souboru pravidel nebo cíl a aktuální adresář neobsahuje soubor s názvem souboru pravidel.  
  
 NMAKE požaduje souboru pravidel nebo příkazového řádku cíl (nebo obě). Chcete-li zpřístupnit souboru pravidel NMAKE, zadejte možnost /F nebo umístit soubor s názvem souboru pravidel v aktuálním adresáři. NMAKE můžete vytvořit cíl příkazového řádku pomocí odvozená pravidla, pokud není k dispozici souboru pravidel.