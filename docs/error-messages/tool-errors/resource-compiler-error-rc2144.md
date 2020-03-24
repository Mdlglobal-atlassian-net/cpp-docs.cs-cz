---
title: Chyba kompilátoru prostředků RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 1b080916642fc1be4b22820668c4cb4137675425
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191194"
---
# <a name="resource-compiler-error-rc2144"></a>Chyba kompilátoru prostředků RC2144

ID primárního jazyka není číslo.

ID primárního jazyka musí být šestnáctkové ID jazyka. Seznam platných ID jazyků naleznete v tématu [řetězce jazyka a země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) v *Referenční příručce ke knihovně run-time* .

K této chybě může dojít také v případě, že byly prostředky přidány a odstraněny z. RC soubor pomocí nástroje. Chcete-li tento problém vyřešit, otevřete. Soubor RC v textovém editoru a čistě nepoužívané prostředky vyčistěte ručně.
