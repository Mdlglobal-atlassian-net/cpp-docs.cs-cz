---
title: Speciální znaky v makrech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a94001e2f912049518120911c25ae64afa24da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721421"
---
# <a name="special-characters-in-macros"></a>Speciální znaky v makrech

Po definici určuje komentář, přihlaste čísla (#). Pokud chcete zadat literální znak čísla v makru, použijte stříšky (^), stejně jako v ^ #.

Znak dolaru ($) určuje volání makra. Pokud chcete nastavit literál $, použijte $$.

Rozšíření definice na nový řádek, ukončení řádku zpětným lomítkem (\\). Při vyvolání makra zpětné lomítko a nový řádek znak je nahrazen mezerou. K určení literálu zpětné lomítko na konci řádku, před stříšky (^) nebo za ním specifikátor komentáře (#).

K určení literálu znakem, končit řádek s stříšky (^), jako:

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Viz také

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)