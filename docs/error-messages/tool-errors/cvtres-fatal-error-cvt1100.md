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
ms.openlocfilehash: ba8ea3fdfdea9ca5aa142a1f2a8f15c5d3ac536a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100
duplicitní prostředků – typ: typ, název: název, jazyk: jazyk, příznaky: příznaky, velikost: velikost  
  
 Daný prostředek byl zadán více než jednou.  
  
 Může se tato chyba, pokud linkeru vytváří knihovny typů a nezadali jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředků ve vašem projektu už používá 1. V takovém případě zadejte /TLBID a zadejte jiné číslo až 65535.