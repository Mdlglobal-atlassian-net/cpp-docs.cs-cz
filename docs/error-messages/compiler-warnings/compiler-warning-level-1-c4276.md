---
title: "Kompilátoru (úroveň 1) upozornění C4276 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4276
dev_langs: C++
helpviewer_keywords: C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 609acf714cc149d7a12d515b991fa78c40244129
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4276"></a>C4276 kompilátoru upozornění (úroveň 1)
'function': žádné prototypu poskytuje; předpokládá, že žádné parametry  
  
 Pokud se vydáte adresu funkce s [__stdcall](../../cpp/stdcall.md) konvence volání, musíte přidělit prototyp, kompilátor můžete vytvořit funkce upravený název. Vzhledem k tomu *funkce* nemá žádné prototypu kompilátoru, při vytváření upravený název, předpokládá funkce nemá žádné parametry.