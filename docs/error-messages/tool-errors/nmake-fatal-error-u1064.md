---
title: Závažná chyba nástroje NMAKE U1064 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5573943fc2c274d48768933a634b2c052361a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1064"></a>Závažná chyba nástroje NMAKE U1064
Nebyl nalezen v souboru pravidel a není zadán žádný cíl.  
  
 Příkaz NMAKE nezadali souboru pravidel nebo cíl a aktuální adresář neobsahuje soubor s názvem souboru pravidel.  
  
 NMAKE požaduje souboru pravidel nebo příkazového řádku cíl (nebo obě). Chcete-li zpřístupnit souboru pravidel NMAKE, zadejte možnost /F nebo umístit soubor s názvem souboru pravidel v aktuálním adresáři. NMAKE můžete vytvořit cíl příkazového řádku pomocí odvozená pravidla, pokud není k dispozici souboru pravidel.