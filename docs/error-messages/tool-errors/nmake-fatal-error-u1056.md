---
title: Závažná chyba nástroje NMAKE U1056 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1056"></a>Závažná chyba nástroje NMAKE U1056
Nelze najít procesor příkazů  
  
 Procesor příkazů nebyla na v zadané cestě **COMSPEC** nebo **cesta** proměnné prostředí.  
  
 NMAKE používá COMMAND.COM nebo CMD. EXE jako procesor příkazů při provádění příkazů. Hledá procesor příkazů nejprve v cestě nastavit **COMSPEC**. Pokud **COMSPEC** neexistuje, hledání NMAKE adresáře zadaný v **CESTU**.