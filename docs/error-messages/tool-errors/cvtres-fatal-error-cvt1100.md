---
title: Závažná chyba nástroje CVTRES CVT1100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32085c4c37c82567eb78f46b52bcc4a6c41daae5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cvtres-fatal-error-cvt1100"></a>Závažná chyba nástroje CVTRES CVT1100
duplicitní prostředků – typ: typ, název: název, jazyk: jazyk, příznaky: příznaky, velikost: velikost  
  
 Daný prostředek byl zadán více než jednou.  
  
 Může se tato chyba, pokud linkeru vytváří knihovny typů a nezadali jste [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) a prostředků ve vašem projektu už používá 1. V takovém případě zadejte /TLBID a zadejte jiné číslo až 65535.