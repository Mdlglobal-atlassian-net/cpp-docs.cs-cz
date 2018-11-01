---
title: Kompilátor upozornění (úroveň 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: a4958bb446b5f7e80ef2eef92b52a0f86cf6a134
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479401"
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilátor upozornění (úroveň 1) C4049

limit kompilátoru: ukončuje se emitování čísla řádku

Tento soubor obsahuje více než 16 777 215 (2<sup>24</sup>-1) zdrojové řádky. Kompilátor se zastaví na 16 777 215 číslování.

Pro kód po řádku 16 777 215:

- Image bude obsahovat žádné informace o ladění pro čísla řádků.

- Některé diagnostiky může být nahlášeno s čísly řádků nesprávné.

- výpisy .asm (/ FAs) může mít nesprávný řádek čísla.