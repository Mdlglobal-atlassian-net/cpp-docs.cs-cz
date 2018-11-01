---
title: Závažná chyba nástroje NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641503"
---
# <a name="nmake-fatal-error-u1051"></a>Závažná chyba nástroje NMAKE U1051

Nedostatek paměti

NMAKE není dostatek paměti, včetně virtuální paměti, protože soubor pravidel je příliš velký nebo složitý.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Uvolněte místo na disku.

1. Zvětšete velikost stránkovacího souboru systému Windows NT nebo odkládací soubor Windows.

1. Pokud pouze část souboru pravidel se používá, rozdělit na samostatné soubory souboru pravidel nebo použít **! Pokud** a omezit tak množství, která musí zpracovávat NMAKE direktivy předběžného zpracování. **! Pokud** direktivy zahrnují **! Pokud**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! OSTATNÍ** `IFDEF`, a **! OSTATNÍ** `IFNDEF`.