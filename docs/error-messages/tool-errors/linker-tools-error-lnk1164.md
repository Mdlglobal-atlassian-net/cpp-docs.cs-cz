---
title: Chyba linkerů LNK1164
ms.date: 11/04/2016
f1_keywords:
- LNK1164
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
ms.openlocfilehash: 8685a9e0eb356719eaab129af9df9a1cc0ebb085
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254950"
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164

část zarovnání oddílu (číslo) větší než hodnota/align.

Velikost zarovnání pro danou část do souboru objektu nepřekročí hodnotu zadanou pomocí [/ALIGN](../../build/reference/align-section-alignment.md) možnost. **/ALIGN** hodnota musí být mocninou čísla 2 a musí být roven nebo překračují zarovnání oddílů v souboru objektu.

Buď zkompilujte znovu s menším zarovnání oddílů nebo zvýšení **/ALIGN** hodnotu.