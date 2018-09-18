---
title: Závažná chyba kompilátoru prostředků RC1052 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1052
dev_langs:
- C++
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef276bdecf675a178f43f22e3aef88f4ed1c73cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071182"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Závažná chyba kompilátoru prostředků RC1052

limit kompilátoru: bloky #if nebo #ifdef jsou vnořené moc hluboko

Program překročil maximální povolenou úrovní vnoření pro `#if` a `#ifdef` direktivy.

Tato chyba může být způsobena podle zahrnují soubory, které používají tyto direktivy preprocesoru.

Chcete-li tento problém vyřešit, snižte počet vnořených `#if` a `#ifdef` direktivy v souboru prostředků. Je-li tento problém hlavičkové soubory, které jsou zahrnuty v souboru prostředků, snižte počet vnořených `#if` a `#ifdef` direktivy v souborech hlaviček. Pokud to není možné, zvažte vytvoření a včetně nový soubor hlaviček v souboru prostředků spuštěním preprocesoru k existujícím souborům zahrnuté záhlaví. Další informace najdete v tématu [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.