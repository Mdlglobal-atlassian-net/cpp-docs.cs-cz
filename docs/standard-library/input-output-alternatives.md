---
title: Vstupně výstupní alternativy
ms.date: 05/07/2019
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
ms.openlocfilehash: 5fb98714a96dedf725ea17332d7c1627e3390896
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221388"
---
# <a name="inputoutput-alternatives"></a>Vstupní/výstupní alternativy

Microsoft C++ kompilátor poskytuje několik alternativ pro vstupně/výstupní programování:

- C knihovny run-time s přímým přístupem, bez vyrovnávací paměti vstupně-výstupních operací.

- ANSI C knihovny run-time stream vstupně-výstupních operací.

- I/O konzoly a portu s přímým přístupem.

- Knihovny Microsoft Foundation Class.

- Knihovny Standard C++ společnosti Microsoft.

Iostream – třídy jsou užitečné pro ukládány do vyrovnávací paměti, formátovaný text vstupně-výstupních operací. Jsou také užitečná pro vstupně-výstupní operace bez vyrovnávací paměti nebo binární Pokud potřebujete C++ rozhraní pro programování a rozhodnot nepoužívat knihovny Microsoft Foundation Class (MFC). Iostream – třídy jsou alternativou objektově orientované vstupně-výstupních operací pro funkce jazyka C za běhu.

Iostream – třídy lze použít s operačním systémem Microsoft Windows. Řetězec a souborů datových proudů fungovat bez omezení, ale objekty znakového režimu datového proudu `cin`, `cout`, `cerr`, a `clog` nejsou konzistentní s grafické uživatelské rozhraní Windows. Můžete také provádět odvozování třídy pro vlastní datové proudy, které komunikují přímo s prostředím Windows.

## <a name="see-also"></a>Viz také:

[Co je stream](../standard-library/what-a-stream-is.md)<br/>
