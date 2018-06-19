---
title: C2919 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5e2eb2a32f1a906814f5b347ba1ebf13eba71ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245799"
---
# <a name="compiler-error-c2919"></a>C2919 chyby kompilátoru
'type': operátory nelze použít na povrchu publikované WinRT typu  
  
 Systém typů prostředí Windows Runtime nepodporuje operátor členské funkce v publikované prostor typu. Je to proto, že ne všechny jazyky spotřebovat operátor členské funkce. Můžete vytvořit privátní nebo interní operátor členské funkce, které lze volat z kódu C++ ve stejné třídě nebo kompilace jednotce.  
  
 Chcete-li tento problém vyřešit, odeberte – členská funkce operátor z veřejné rozhraní nebo změňte jej na pojmenované členské funkce. Například místo z `operator==`, název členské funkce `Equals`.