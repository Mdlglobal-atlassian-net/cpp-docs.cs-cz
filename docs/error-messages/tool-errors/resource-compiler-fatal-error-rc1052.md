---
title: Závažná chyba kompilátoru prostředků RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: ad0fe23b20870610c5979d6ad85fce55b4e506d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182553"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Závažná chyba kompilátoru prostředků RC1052

limit kompilátoru: bloky #if nebo #ifdef jsou vnořené moc hluboko.

Program překročil maximální povolený počet vnořených úrovní pro direktivy `#if` a `#ifdef`.

Tato chyba může být způsobena zahrnutím souborů, které používají tyto direktivy preprocesoru.

Chcete-li tento problém vyřešit, snižte počet vnořených direktiv `#if` a `#ifdef` v souboru prostředků. Pokud je problém způsoben soubory hlaviček, které jsou zahrnuty v souboru prostředků, snižte počet vnořených `#if` a `#ifdef` direktiv v hlavičkových souborech. Pokud to není možné, zvažte vytvoření a zahrnutí nového hlavičkového souboru do souboru prostředků tak, že spustíte preprocesor pro existující zahrnuté soubory hlaviček. Další informace naleznete v tématu [/p (předzpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.
