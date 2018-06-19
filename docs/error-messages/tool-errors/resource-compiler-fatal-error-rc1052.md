---
title: Závažná chyba kompilátoru prostředků RC1052 | Microsoft Docs
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
ms.openlocfilehash: 6e0651f8c2b48ea69e7137ffa3415ddaffd8fe44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319907"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Závažná chyba kompilátoru prostředků RC1052
omezení kompilátoru: #if nebo #ifdef bloky vnořeny příliš hluboko  
  
 Program překročil maximální povolenou vnořených úrovní v `#if` a `#ifdef` direktivy.  
  
 Tato chyba může být způsobena ve obsahují soubory, které používají tyto preprocesor – direktivy.  
  
 Chcete-li tento problém vyřešit, snižte počet vnořených `#if` a `#ifdef` direktivy v souboru prostředků. Pokud tento problém je způsoben hlavičkových souborů, které jsou součástí souboru prostředků, snižte počet vnořených `#if` a `#ifdef` direktivy v hlavičkových souborů. Pokud to není možné, zvažte vytvoření a včetně nový soubor záhlaví v souboru prostředků spuštěním preprocesor na existující soubory zahrnuté záhlaví. Další informace najdete v tématu [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.