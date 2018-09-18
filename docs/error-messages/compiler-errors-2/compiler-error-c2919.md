---
title: Chyba kompilátoru C2919 | Dokumentace Microsoftu
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
ms.openlocfilehash: 5d6ee01e32cd1855855fa6ac071af159be8bac0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106828"
---
# <a name="compiler-error-c2919"></a>Chyba kompilátoru C2919

'type': operátory nejde používat na publikované ploše typu WinRT

Systém typů prostředí Windows Runtime nepodporuje operátor členské funkce v publikované ploše typu. Je to proto, že ne všechny jazyky můžou využívat funkce členského operátora. Můžete vytvořit privátní nebo interní operátor členské funkce, které lze volat z kódu jazyka C++ ve stejné jednotce třídy nebo kompilace.

Chcete tento problém vyřešit, odeberte členské funkce operátora z veřejného rozhraní nebo ji změňte na pojmenované členskou funkci. Například namísto z `operator==`, název členské funkce `Equals`.