---
title: Chyba kompilátoru C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: 624b3ab47ccb1c934b612ec8648b5eee0d233690
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176972"
---
# <a name="compiler-error-c2919"></a>Chyba kompilátoru C2919

Type: operátory nejde používat na publikované ploše typu WinRT.

Systém typů prostředí Windows Runtime nepodporuje funkce členů operátoru na publikované ploše typu. Důvodem je, že ne všechny jazyky mohou spotřebovávat členské funkce operátoru. Můžete vytvořit soukromé nebo interní členské funkce operátoru, které mohou být volány z C++ kódu ve stejné třídě nebo kompilační jednotce.

Chcete-li tento problém vyřešit, odeberte členskou funkci operátora z veřejného rozhraní nebo ji změňte na pojmenovanou členskou funkci. Například namísto `operator==`název členské funkce `Equals`.
