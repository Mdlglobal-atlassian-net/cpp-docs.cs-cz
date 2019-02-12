---
title: Chyby pozice souboru
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: 3d581d86d6f08eee564feb6373a623512085ccca
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147799"
---
# <a name="file-position-errors"></a>Chyby pozice souboru

**ANSI 4.9.9.1, 4.9.9.4** hodnota, na kterou makro `errno` se nastavil `fgetpos` nebo `ftell` při selhání

Když `fgetpos` nebo `ftell` selže, `errno` je nastavena na hodnotu konstanty manifestu `EINVAL` li pozice neplatná nebo `EBADF` je-li číslo souboru chybné. Konstanty jsou definovány v ERRNO.H.

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
