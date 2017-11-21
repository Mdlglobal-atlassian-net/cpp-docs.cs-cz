---
title: "Závažná chyba kompilátoru prostředků RC1052 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1052
dev_langs: C++
helpviewer_keywords: RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20ffe772cc7a7fbdc96b10c16d542a6874b54577
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Závažná chyba kompilátoru prostředků RC1052
omezení kompilátoru: #if nebo #ifdef bloky vnořeny příliš hluboko  
  
 Program překročil maximální povolenou vnořených úrovní v `#if` a `#ifdef` direktivy.  
  
 Tato chyba může být způsobena ve obsahují soubory, které používají tyto preprocesor – direktivy.  
  
 Chcete-li tento problém vyřešit, snižte počet vnořených `#if` a `#ifdef` direktivy v souboru prostředků. Pokud tento problém je způsoben hlavičkových souborů, které jsou součástí souboru prostředků, snižte počet vnořených `#if` a `#ifdef` direktivy v hlavičkových souborů. Pokud to není možné, zvažte vytvoření a včetně nový soubor záhlaví v souboru prostředků spuštěním preprocesor na existující soubory zahrnuté záhlaví. Další informace najdete v tématu [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru.