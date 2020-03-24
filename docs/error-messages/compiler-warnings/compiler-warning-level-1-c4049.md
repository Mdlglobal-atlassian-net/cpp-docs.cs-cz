---
title: Upozornění kompilátoru (úroveň 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164141"
---
# <a name="compiler-warning-level-1-c4049"></a>Upozornění kompilátoru (úroveň 1) C4049

limit kompilátoru: ukončení emisí čísla řádku

Soubor obsahuje více než 16 777 215 (2<sup>24</sup>-1) zdrojové řádky. Kompilátor zastaví číslování v 16 777 215.

Pro kód po řádku 16 777 215:

- Obrázek nebude obsahovat žádné ladicí informace pro čísla řádků.

- Některé diagnostiky mohou být hlášeny s nesprávnými čísly řádků.

- výpisy. asm (/FAs) můžou mít nesprávná čísla řádků.
