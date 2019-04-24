---
title: Závažná chyba kompilátoru prostředků RC1015
ms.date: 11/04/2016
f1_keywords:
- RC1015
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
ms.openlocfilehash: f20101c2edc4da132c89dcda451c71af2304a13d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297655"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Závažná chyba kompilátoru prostředků RC1015

nejde otevřít vložený soubor 'filename'

Daný vloženého souboru neexistuje, nelze otevřít nebo se nenašel.

Ujistěte se, že nastavení prostředí jsou platná a zda je zadán správnou cestu k souboru. Ujistěte se, že jsou k dispozici pro kompilátor prostředků dostatek popisovačů souborů. Pokud je soubor na síťové jednotce, ujistěte se, že máte oprávnění k otevření souboru.

RC1015 může dojít i v případě, že tento soubor existuje v adresáři zadaném jako další zahrnout adresář ve vlastnosti konfigurace -> prostředků -> stránce Obecné vlastnosti; Zadejte úplnou cestu k souboru include.
