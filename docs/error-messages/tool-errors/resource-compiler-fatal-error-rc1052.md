---
title: Závažná chyba kompilátoru prostředků RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: 2ab9dd48420ca263abbf3da22da878a3e74a2151
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297291"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Závažná chyba kompilátoru prostředků RC1052

limit kompilátoru: bloky #if nebo #ifdef jsou vnořené moc hluboko

Program překročil maximální povolenou úrovní vnoření pro `#if` a `#ifdef` direktivy.

Tato chyba může být způsobena podle zahrnují soubory, které používají tyto direktivy preprocesoru.

Chcete-li tento problém vyřešit, snižte počet vnořených `#if` a `#ifdef` direktivy v souboru prostředků. Je-li tento problém hlavičkové soubory, které jsou zahrnuty v souboru prostředků, snižte počet vnořených `#if` a `#ifdef` direktivy v souborech hlaviček. Pokud to není možné, zvažte vytvoření a včetně nový soubor hlaviček v souboru prostředků spuštěním preprocesoru k existujícím souborům zahrnuté záhlaví. Další informace najdete v tématu [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.