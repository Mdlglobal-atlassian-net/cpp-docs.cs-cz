---
title: Závažná chyba kompilátoru prostředků RC1015 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0456845152fb2879d2f58c9c40af2562c7207535
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890241"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Závažná chyba kompilátoru prostředků RC1015

nejde otevřít vložený soubor 'filename'

Daný vloženého souboru neexistuje, nelze otevřít nebo se nenašel.

Ujistěte se, že nastavení prostředí jsou platná a zda je zadán správnou cestu k souboru. Ujistěte se, že jsou k dispozici pro kompilátor prostředků dostatek popisovačů souborů. Pokud je soubor na síťové jednotce, ujistěte se, že máte oprávnění k otevření souboru.

RC1015 může dojít i v případě, že tento soubor existuje v adresáři zadaném jako další zahrnout adresář ve vlastnosti konfigurace -> prostředků -> stránce Obecné vlastnosti; Zadejte úplnou cestu k souboru include.
