---
title: Chyba kompilátoru C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: ab11226c8cc4629a265dd182d5f882f6b3be7e5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577655"
---
# <a name="compiler-error-c2919"></a>Chyba kompilátoru C2919

'type': operátory nejde používat na publikované ploše typu WinRT

Systém typů prostředí Windows Runtime nepodporuje operátor členské funkce v publikované ploše typu. Je to proto, že ne všechny jazyky můžou využívat funkce členského operátora. Můžete vytvořit privátní nebo interní operátor členské funkce, které lze volat z kódu jazyka C++ ve stejné jednotce třídy nebo kompilace.

Chcete tento problém vyřešit, odeberte členské funkce operátora z veřejného rozhraní nebo ji změňte na pojmenované členskou funkci. Například namísto z `operator==`, název členské funkce `Equals`.