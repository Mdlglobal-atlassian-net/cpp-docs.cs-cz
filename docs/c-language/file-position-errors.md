---
title: Chyby pozice souboru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1bcb4db45f17c9e2d697ee63912e63efe6e8176c
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="file-position-errors"></a>Chyby pozice souboru
**ANSI 4.9.9.1, 4.9.9.4** hodnotu, do které makro `errno` se nastavuje pomocí `fgetpos` nebo `ftell` funkce při selhání  
  
 Když `fgetpos` nebo `ftell` selže, `errno` je nastaven na konstantu manifestu `EINVAL` Pokud pozici je neplatný nebo `EBADF` Pokud číslo soubor je chybný. Konstanty jsou definovány v ERRNO.H.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)
