---
title: Chyby pozice souboru | Microsoft Docs
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
ms.openlocfilehash: 71c059939891680b638e8644f7902d54452f5332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383214"
---
# <a name="file-position-errors"></a>Chyby pozice souboru
**ANSI 4.9.9.1, 4.9.9.4** hodnotu, do které makro `errno` se nastavuje pomocí `fgetpos` nebo `ftell` funkce při selhání  
  
 Když `fgetpos` nebo `ftell` selže, `errno` je nastaven na konstantu manifestu `EINVAL` Pokud pozici je neplatný nebo `EBADF` Pokud číslo soubor je chybný. Konstanty jsou definovány v ERRNO.H.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)
