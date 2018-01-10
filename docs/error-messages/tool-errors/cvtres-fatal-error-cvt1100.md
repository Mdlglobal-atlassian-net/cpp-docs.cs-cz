---
title: "Závažná chyba nástroje CVTRES CVT1100 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CVT1100
dev_langs: C++
helpviewer_keywords: CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 906e03b778276196d36a04e6b9e2f02a2d5944bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100
duplicitní prostředků – typ: typ, název: název, jazyk: jazyk, příznaky: příznaky, velikost: velikost  
  
 Daný prostředek byl zadán více než jednou.  
  
 Může se tato chyba, pokud linkeru vytváří knihovny typů a nezadali jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředků ve vašem projektu už používá 1. V takovém případě zadejte /TLBID a zadejte jiné číslo až 65535.