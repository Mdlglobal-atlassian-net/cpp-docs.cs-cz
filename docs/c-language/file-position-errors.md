---
title: Chyby pozice souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8def11317548bfd6e70badab4563891c1b6f864d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031903"
---
# <a name="file-position-errors"></a>Chyby pozice souboru

**ANSI 4.9.9.1, 4.9.9.4** hodnota, na kterou makro `errno` se nastavil `fgetpos` nebo `ftell` při selhání

Když `fgetpos` nebo `ftell` selže, `errno` je nastavena na hodnotu konstanty manifestu `EINVAL` li pozice neplatná nebo `EBADF` je-li číslo souboru chybné. Konstanty jsou definovány v ERRNO.H.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)
