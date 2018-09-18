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
ms.openlocfilehash: 7a72cba53ebe9a286ac2e7cbbf2c41b78f4e4e08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100759"
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Závažná chyba kompilátoru prostředků RC1015

nejde otevřít vložený soubor 'filename'

Daný vloženého souboru neexistuje, nelze otevřít nebo se nenašel.

Ujistěte se, že nastavení prostředí jsou platná a zda je zadán správnou cestu k souboru. Ujistěte se, že jsou k dispozici pro kompilátor prostředků dostatek popisovačů souborů. Pokud je soubor na síťové jednotce, ujistěte se, že máte oprávnění k otevření souboru.

RC1015 může dojít i v případě, že tento soubor existuje v adresáři zadaném jako další zahrnout adresář ve vlastnosti konfigurace -> prostředků -> stránce Obecné vlastnosti; Zadejte úplnou cestu k souboru include.

Další informace najdete v článku znalostní báze Q326987: RC1015 chyby při použití prostředků zobrazení Pokud cesty zahrnutí je příliš dlouhý.