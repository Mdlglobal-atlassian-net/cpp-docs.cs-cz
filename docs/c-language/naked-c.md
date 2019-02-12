---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 519d7bceb700e9862f0d0025b755cf28fb0fbc0c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149775"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft Specific**

Atribut třídy úložiště naked je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště naked generuje kompilátor kód bez kódu prologu a epilogu. Neviditelné funkce jsou užitečné, potřebujete-li napsat vlastní sekvence kódu prologu a epilogu pomocí vloženého kódu assembleru. Neviditelné funkce jsou užitečné k psaní ovladačů virtuálních zařízení.

Konkrétní informace o použití atributu naked naleznete v tématu [neviditelné funkce](../c-language/naked-functions.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)
