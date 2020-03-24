---
title: Závažná chyba C1061
ms.date: 11/04/2016
f1_keywords:
- C1061
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
ms.openlocfilehash: 049adb38dd8f33de7dbdd02d8420eba284ca2ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204409"
---
# <a name="fatal-error-c1061"></a>Závažná chyba C1061

Omezení kompilátoru: bloky jsou vnořeny příliš hluboko

Vnoření bloků kódu překračuje limit 128 úrovní vnoření. Jedná se o pevný limit kompilátoru pro jazyky C a C++ v 32bitové i 64bitové sadě nástrojů. Počet úrovní vnoření lze zvýšit pomocí čehokoli, co vytvoří obor nebo blok. Úroveň vnoření, kterou pozoruje kompilátor, dokážou zvýšit například obory názvů, direktivy using, rozšíření preprocesoru, rozšíření šablon, zpracování výjimek, konstrukce smyček a klauzule else-if.

Chcete-li tuto chybu vyřešit, musíte kód refaktorovat. Hluboce vnořený kód je v každém případě obtížně pochopitelný a odůvodnitelný. Refaktoring kódu tak, aby měl menší počet úrovní vnoření, může vylepšit kvalitu kódu a zjednodušit údržbu. Hluboce vnořený kód rozdělte na funkce, které jsou volány z původního kontextu. Omezte počet smyček nebo zřetězených klauzulí else-if uvnitř bloku.
