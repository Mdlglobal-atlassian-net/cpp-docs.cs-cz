---
title: Speciální znaky v makrech
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: aac7b07500d2a129194e7234210a590cb5d0f19a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823053"
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

[Definice makra NMAKE](defining-an-nmake-macro.md)
