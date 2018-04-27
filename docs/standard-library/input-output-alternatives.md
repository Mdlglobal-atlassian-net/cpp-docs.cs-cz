---
title: Vstupní výstupní alternativy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 292f47f1431b1c184f972d87ab85c078297822d5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="inputoutput-alternatives"></a>Vstupní/výstupní alternativy

Visual C++ nabízí další pro programování vstupně-výstupních operací:

- C běhové knihovny přímé, bez vyrovnávací paměti vstupně-výstupní operace.

- Datový proud běhové knihovny ANSI C vstupně-výstupní operace.

- Konzoly a portu přímé vstupy/výstupy.

- Microsoft Foundation Class Library.

- Microsoft standardní knihovna C++.

Iostream, které jsou užitečné pro třídy uložená do vyrovnávací paměti, formátovaný text vstupně-výstupní operace. Jsou užitečné také pro vstupně-výstupní operace bez vyrovnávací paměti nebo binary Pokud potřebujete programovací rozhraní jazyka C++ a nechcete používat knihovny Microsoft Foundation Class (MFC). Iostream – třídy jsou alternativou objektově orientované vstupně-výstupních operací na běhové funkce C.

Iostream – třídy můžete použít s operačním systémem Microsoft Windows. Datové proudy řetězec a soubor fungovat bez omezení, ale objekty znakového režimu datového proudu `cin`, `cout`, `cerr`, a `clog` nejsou konzistentní s grafické uživatelské rozhraní systému Windows. Můžete také odvozovat vlastní datový proud třídy, které komunikovat přímo s prostředí systému Windows.

## <a name="see-also"></a>Viz také

[Co je stream](../standard-library/what-a-stream-is.md)<br/>
