---
title: Závažná chyba nástroje NMAKE U1073 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dde9ca2f4a15edf6599dcc31b39d9411645f2a6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1073"></a>Závažná chyba nástroje NMAKE U1073
Nevíte, jak provádět 'targetname.  
  
 Zadaný cílový neexistuje a není žádný příkaz k provedení nebo odvozené pravidlo použít.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zkontrolujte, zda název cílové.  
  
2.  Pokud *targetname* je pseudotarget, zadejte jako cíl v jiném popis bloku.  
  
3.  Pokud *targetname* je vyvolání typu makro, ujistěte se, nerozšiřuje řetězec null.