---
title: Závažná chyba C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 1733a13e697af775653609ddfcc22f7297dad240
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661172"
---
# <a name="fatal-error-c1061"></a>Závažná chyba C1061

Omezení kompilátoru: bloky jsou vnořeny příliš hluboko

Vnoření bloků kódu překračuje limit 128 úrovní vnoření. Jedná se o pevný limit kompilátoru pro jazyky C a C++ v 32bitové i 64bitové sadě nástrojů. Počet úrovní vnoření lze zvýšit pomocí čehokoli, co vytvoří obor nebo blok. Úroveň vnoření, kterou pozoruje kompilátor, dokážou zvýšit například obory názvů, direktivy using, rozšíření preprocesoru, rozšíření šablon, zpracování výjimek, konstrukce smyček a klauzule else-if.

Chcete-li tuto chybu vyřešit, musíte kód refaktorovat. Hluboce vnořený kód je v každém případě obtížně pochopitelný a odůvodnitelný. Refaktoring kódu tak, aby měl menší počet úrovní vnoření, může vylepšit kvalitu kódu a zjednodušit údržbu. Hluboce vnořený kód rozdělte na funkce, které jsou volány z původního kontextu. Omezte počet smyček nebo zřetězených klauzulí else-if uvnitř bloku.