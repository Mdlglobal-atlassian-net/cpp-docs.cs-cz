---
title: Upozornění kompilátoru (úroveň 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 295a183afb24121a2abefd336f6ea92110220155
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185501"
---
# <a name="compiler-warning-level-3-c4622"></a>Upozornění kompilátoru (úroveň 3) C4622

přepisují se ladicí informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: ' file '

Informace CodeView v zadaném souboru byly ztraceny, když byly zkompilovány pomocí možnosti [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (použití předkompilovaných hlaviček).

Přejmenujte soubor objektu (pomocí [/FO](../../build/reference/fo-object-file-name.md)) při vytváření nebo používání souboru předkompilované hlavičky a propojte ho pomocí nového objektu.
