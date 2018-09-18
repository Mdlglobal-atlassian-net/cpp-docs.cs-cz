---
title: Závažná chyba nástroje NMAKE U1051 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3d3a14b75a30aa22bcc9faafb97a218051bb080
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045013"
---
# <a name="nmake-fatal-error-u1051"></a>Závažná chyba nástroje NMAKE U1051

Nedostatek paměti

NMAKE není dostatek paměti, včetně virtuální paměti, protože soubor pravidel je příliš velký nebo složitý.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Uvolněte místo na disku.

1. Zvětšete velikost stránkovacího souboru systému Windows NT nebo odkládací soubor Windows.

1. Pokud pouze část souboru pravidel se používá, rozdělit na samostatné soubory souboru pravidel nebo použít **! Pokud** a omezit tak množství, která musí zpracovávat NMAKE direktivy předběžného zpracování. **! Pokud** direktivy zahrnují **! Pokud**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! OSTATNÍ** `IFDEF`, a **! OSTATNÍ** `IFNDEF`.