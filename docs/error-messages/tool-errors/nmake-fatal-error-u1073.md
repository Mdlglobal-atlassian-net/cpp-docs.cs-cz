---
title: "Závažná chyba nástroje NMAKE U1073 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faae317df44560991a88d47ec7f123e6a8126429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1073"></a>Závažná chyba nástroje NMAKE U1073
Nevíte, jak provádět 'targetname.  
  
 Zadaný cílový neexistuje a není žádný příkaz k provedení nebo odvozené pravidlo použít.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zkontrolujte, zda název cílové.  
  
2.  Pokud *targetname* je pseudotarget, zadejte jako cíl v jiném popis bloku.  
  
3.  Pokud *targetname* je vyvolání typu makro, ujistěte se, nerozšiřuje řetězec null.