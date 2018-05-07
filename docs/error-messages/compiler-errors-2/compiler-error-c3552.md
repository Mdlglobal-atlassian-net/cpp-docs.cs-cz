---
title: C3552 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5f1453a6175019ad7c90471330d11c77da26134
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3552"></a>C3552 chyby kompilátoru
'typename': pozdní zadaný návratový typ nemůže obsahovat 'auto'  
  
 Pokud použijete `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat návratový typ pozdní zadaný. Však nelze použít jiný `auto` – klíčové slovo k určení pozdní určených pro návratovým typem. Například následující fragment kódu vypočítá chyba C3552.  
  
 `auto myFunction->auto; // C3552`