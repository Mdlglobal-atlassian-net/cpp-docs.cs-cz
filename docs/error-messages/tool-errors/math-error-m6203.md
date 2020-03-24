---
title: Chyba matematické operace M6203
ms.date: 11/04/2016
f1_keywords:
- M6203
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
ms.openlocfilehash: 371a6c673826c6ce71d7a0eb3b9e08d9488f53f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193690"
---
# <a name="math-error-m6203"></a>Chyba matematické operace M6203

' function ': Chyba _OVERFLOW

Daný výsledek funkce byl příliš velký, aby jej bylo možné znázornit.

Tato chyba volá funkci `_matherr` s názvem funkce, jejími argumenty a typem chyby. Můžete přepsat funkci `_matherr` a přizpůsobit tak zpracování určitých matematických chyb s plovoucí desetinnou čárkou v době běhu.
