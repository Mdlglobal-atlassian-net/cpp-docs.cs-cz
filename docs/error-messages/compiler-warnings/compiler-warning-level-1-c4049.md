---
title: Upozornění (úroveň 1) C4049 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a89d02129e5e8fbedb0649fff0cfe3813304c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053515"
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilátor upozornění (úroveň 1) C4049

limit kompilátoru: ukončuje se emitování čísla řádku

Tento soubor obsahuje více než 16 777 215 (2<sup>24</sup>-1) zdrojové řádky. Kompilátor se zastaví na 16 777 215 číslování.

Pro kód po řádku 16 777 215:

- Image bude obsahovat žádné informace o ladění pro čísla řádků.

- Některé diagnostiky může být nahlášeno s čísly řádků nesprávné.

- výpisy .asm (/ FAs) může mít nesprávný řádek čísla.