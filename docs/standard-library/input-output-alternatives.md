---
title: Alternativy vstupu a výstupu
ms.date: 05/07/2019
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: b46ff242fc263be5069eb691dd0ea9e8fb00b0f9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455293"
---
# <a name="inputoutput-alternatives"></a>Vstupní/výstupní alternativy

Kompilátor společnosti C++ Microsoft nabízí několik alternativ pro vstupně-výstupní programování:

- Běhová knihovna C – přímé, neuložený vstup/výstup do vyrovnávací paměti.

- I/O Stream knihovny runtime ANSI C.

- Vstupně-výstupní operace s konzolou a portem

- Knihovna Microsoft Foundation Class.

- Standardní C++ knihovna Microsoft.

Třídy iostream – jsou užitečné pro ukládání do vyrovnávací paměti formátovaného textu v/v. Jsou také užitečné pro nebufferované nebo binární I výstupní operace, pokud potřebujete C++ programovací rozhraní a rozhodnete se nepoužívat knihovnu Microsoft Foundation Class (MFC). Třídy iostream – jsou uživatelsky orientované alternativou vstupně-výstupních operací pro běhové funkce jazyka C.

Třídy iostream – můžete používat s operačním systémem Microsoft Windows. Datové proudy řetězců `cin`a souborů fungují bez omezení, ale objekty `cout` `cerr`datového proudu v režimu znaků, a `clog` jsou nekonzistentní s grafickým uživatelským rozhraním systému Windows. Můžete také odvodit vlastní třídy streamu, které komunikují přímo s prostředím Windows.

## <a name="see-also"></a>Viz také:

[Co je stream](../standard-library/what-a-stream-is.md)
