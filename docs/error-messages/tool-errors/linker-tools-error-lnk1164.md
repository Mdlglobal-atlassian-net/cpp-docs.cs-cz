---
title: Chyba linkerů LNK1164
ms.date: 11/04/2016
f1_keywords:
- LNK1164
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
ms.openlocfilehash: 5f32fbd455faff449f57cfb9bb38009b03005913
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184031"
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164

zarovnání oddílu oddílu (číslo) je větší než hodnota/ALIGN

Velikost zarovnání pro daný oddíl v souboru objektu překračuje hodnotu zadanou pomocí možnosti [/align](../../build/reference/align-section-alignment.md) . Hodnota **/align** musí být mocnina 2 a musí být rovna nebo větší než zarovnání oddílu zadané v souboru objektu.

Buď znovu zkompilujte s menším zarovnáním oddílu, nebo zvyšte hodnotu **/align** .
