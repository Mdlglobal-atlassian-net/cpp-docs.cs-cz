---
title: Chyby pozice souboru
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: f8c1d5dfc6a599533ce8c1dcfa624d2595779f2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554606"
---
# <a name="file-position-errors"></a>Chyby pozice souboru

**ANSI 4.9.9.1, 4.9.9.4** hodnota, na kterou makro `errno` se nastavil `fgetpos` nebo `ftell` při selhání

Když `fgetpos` nebo `ftell` selže, `errno` je nastavena na hodnotu konstanty manifestu `EINVAL` li pozice neplatná nebo `EBADF` je-li číslo souboru chybné. Konstanty jsou definovány v ERRNO.H.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)
