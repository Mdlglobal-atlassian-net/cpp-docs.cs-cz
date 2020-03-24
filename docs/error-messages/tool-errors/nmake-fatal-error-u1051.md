---
title: Závažná chyba nástroje NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193677"
---
# <a name="nmake-fatal-error-u1051"></a>Závažná chyba nástroje NMAKE U1051

nedostatek paměti

V nástroji NMAKE došlo k nedostatku paměti, včetně virtuální paměti, protože soubor pravidel byl příliš velký nebo složitý.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Uvolněte místo na disku.

1. Zvětšete velikost stránkovacího souboru systému Windows NT nebo souboru Windows swap.

1. Je-li použita pouze část souboru pravidel, rozdělte soubor pravidel do samostatných souborů nebo použijte možnost **! Pokud** direktivy předběžného zpracování omezují množství, které musí NMAKE zpracovat. **. Pokud** direktivy zahrnují **! Pokud**je, `!IFDEF` **! IFNDEF**, **! JINAK, pokud**, **! JINAK** `IFDEF`a **! JINAK** `IFNDEF`.
