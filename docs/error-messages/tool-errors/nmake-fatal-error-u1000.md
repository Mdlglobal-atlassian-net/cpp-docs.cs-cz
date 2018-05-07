---
title: Závažná chyba nástroje NMAKE U1000 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1000
dev_langs:
- C++
helpviewer_keywords:
- U1000
ms.assetid: 49b9bd9e-f1bc-4b55-a171-c748e40b195e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a8d4e0f150d82482dd8391efa1f2251ac37bc8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1000"></a>Závažná chyba nástroje NMAKE U1000
Chyba syntaxe: ')' chybí v volání – makro  
  
 Levé závorky, **(**, výsledná bez odpovídající pravé závorky **)**, v makro volání. Správný tvar je **$(***název***)**; `$` *n* je povolen pro názvy jeden znak.