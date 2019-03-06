---
title: Speciální znaky v makrech
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: d20c88b2223732177d79e676262a3c43eb8054a9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418724"
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

## <a name="see-also"></a>Viz také:

[Definice makra NMAKE](../build/defining-an-nmake-macro.md)
