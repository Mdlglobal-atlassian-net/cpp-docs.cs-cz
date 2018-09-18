---
title: Naked (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6665bafb0041989e99a3a766204555f969d16c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062147"
---
# <a name="naked-c"></a>Naked (C)

**Specifické pro Microsoft**

Atribut třídy úložiště naked je rozšíření jazyka C specifické pro společnost Microsoft. Pro funkce deklarované s atributem třídy úložiště naked generuje kompilátor kód bez kódu prologu a epilogu. Neviditelné funkce jsou užitečné, potřebujete-li napsat vlastní sekvence kódu prologu a epilogu pomocí vloženého kódu assembleru. Neviditelné funkce jsou užitečné k psaní ovladačů virtuálních zařízení.

Konkrétní informace o použití atributu naked naleznete v tématu [neviditelné funkce](../c-language/naked-functions.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)