---
title: Kompilátoru (úroveň 1) upozornění C4276 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afedab27c2fb93075aa33053c12ec6973824f144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277303"
---
# <a name="compiler-warning-level-1-c4276"></a>C4276 kompilátoru upozornění (úroveň 1)
'function': žádné prototypu poskytuje; předpokládá, že žádné parametry  
  
 Pokud se vydáte adresu funkce s [__stdcall](../../cpp/stdcall.md) konvence volání, musíte přidělit prototyp, kompilátor můžete vytvořit funkce upravený název. Vzhledem k tomu *funkce* nemá žádné prototypu kompilátoru, při vytváření upravený název, předpokládá funkce nemá žádné parametry.